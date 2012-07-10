PRODUCTION_WAR="sbin-0.0.2.war"
CONNECTION="sbinConnection"
PORT="8079"

desc "run the app"
task :run do
  sh "mvn jetty:run -Djetty.port="+PORT
end

desc "test cases"
task :test do
  sh "mvn test"
end

desc "clean up"
task :clean do
  sh "rm -rf deployment/"
  sh "rm -rf target/"
end

namespace :package do
  desc "package for production"
  task :production do
    TO_ADD="<Set name=\"war\"><SystemProperty name=\"jetty.home\" default=\".\"/>/webapps/"+PRODUCTION_WAR+"</Set><Set name=\"connectorNames\"><Array type=\"String\"><Item>"+CONNECTION+"</Item></Array></Set></Configure>"
    JETTY_WEB="src/main/webapp/WEB-INF/jetty-web.xml"
    sh "cp "+JETTY_WEB+" tmp.xml"
    sh "cat tmp.xml | sed \'s#</Configure># #' > "+JETTY_WEB
    File.open(JETTY_WEB, 'a') {|f| f.write(TO_ADD) }
    sh "mvn package"
    sh "mv tmp.xml "+JETTY_WEB
    sh "mkdir -p deployment"
    sh "cp target/"+PRODUCTION_WAR+" deployment/"
    puts "the war file is located in deployment/"+PRODUCTION_WAR+"\n"
  end
end

desc "package for the server (Production)"
task :package do
  Rake::Task['package:production'].invoke
end
