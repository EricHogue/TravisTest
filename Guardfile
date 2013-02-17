notification :off

guard 'phpunit', :cli => '--colors', :tests_path => 'tests',
		:keep_failed => true, :all_after_pass => true do

  watch(%r{^tests/.+Test\.php$})
  watch(%r{^src/(.+)\.php$}) { |m| "tests/#{m[1]}Test.php" }
end

guard 'shell' do
    watch(%r{^.+\.php$}) {|m|
        p "Lint check for #{m[0]}"
        `php -l #{m[0]}`
        true
    }
    watch(%r{^.+\.php$}) {
        p "Generating ctags"
        `ctags -R`
        true
    }
end