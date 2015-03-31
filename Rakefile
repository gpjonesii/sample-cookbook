desc 'Run all acceptance tests'
task accept: [:syntax, :lint, :unit]

desc 'Syntax check using knife'
task :syntax do
  sh 'knife cookbook test -o . -a'
end

desc 'Run linting tools -- foodcritic and rubocop'
task :lint do
  sh 'foodcritic -X spec .'
  sh 'rubocop'
end

desc 'Run unit tests with ChefSpec'
task :unit do
  sh 'rspec --color -fd'
end

desc 'Run functional tests with Serverspec'
task :functional do
  sh 'kitchen test'
end

begin
  require "kitchen/rake_tasks"
  Kitchen::RakeTasks.new
rescue LoadError
  puts ">>>>> Kitchen gem not loaded, omitting tasks" unless ENV["CI"]
end
