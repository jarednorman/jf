# jf

Run commands based on things.

## Installation

Put `jf` somewhere in your path. Add something like `nnoremap <leader>t :!jf
test %:.<cr><cr>` to your `.vimrc`. Make sure to add `.jf` and `.jfwin` to your
global git ignores.

## Example `.jf` file for a Rails project

```
task "test" do
  match %r(^spec/.+_spec.rb$) do |m|
    "bundle exec spring rspec #{m[0]}"
  end

  match %r{^app/(.+)\.rb$} do |m|
    "bundle exec spring rspec spec/#{m[1]}_spec.rb"
  end

  match %r{^lib/(.+)\.rb$} do |m|
    "bundle exec spring rspec spec/lib/#{m[1]}_spec.rb"
  end
end
```
