desc 'Start Jekyll server and watch Sass/Bourbon files'
task :s do
  puts "***************************************************"
  puts "* Starting Jekyll server and watching Sass files. *"
  puts "***************************************************"
  jekyllPid = Process.spawn('jekyll serve --watch')
  sassPid = Process.spawn('sass --watch css/scss:css')

  trap("INT") {
    [jekyllPid, sassPid].each { |pid| Process.kill(9, pid) rescue Errno::ESRCH }
    exit 0
  }

  [jekyllPid, sassPid].each { |pid| Process.wait(pid) }
end
