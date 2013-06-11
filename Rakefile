directory "tmp"

task :default => ['morning:turn_off_alarm']

file "tmp/hello.tmp" => "tmp" do
  sh "echo 'Hello' >> 'tmp/hello.tmp'"
end

namespace :morning do
  desc 'Turn off the alarm'
  task :turn_off_alarm do
    puts "Turned off alarm. Would have liked 5 more minutes, though."
  end

  desc 'Groom myself'
  task :groom_myself do
    puts "Brushed teeth."
    puts "Showered."
    puts "Shaved."
  end
  
  desc 'Make Coffee'
  task :make_coffee do
    cups = ENV["COFFEE_CUPS"] || 2
    puts "Made #{cups} cups of coffee. Shakes are gone."
  end

  desc 'Walk the dog'
  task :walk_dog do 
    puts "Dog walked."
  end

  desc 'Get ready for the day => [:turn_off_alarm, :groom_myself, :make_coffee]'
  task :ready_for_the_day => [:turn_off_alarm, :groom_myself, :make_coffee] do
    puts "Ready for the day!"
  end
end

namespace :morning do
  task :groom_myself do
    puts 'Style hair'
  end
end

namespace :afternoon do
  task :make_coffee do
    Rake::Task['morning:make_coffee'].invoke
    puts "Ready for the rest of the day!"
  end
end
