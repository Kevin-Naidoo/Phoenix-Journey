# Phoenix-Journey
  ## Install postgresql and its dependancy <br>
  
  1) `sudo apt install postgresql postgresql-contrib` <br>
  
  2) `sudo apt install inotify-tools` <br>
  
  3) `sudo -u postgres psql` <br>
  
  ## Head into Postgres Terminal and set up the password
  
  4) `\password` <br>
* set-up the desired password,
    *  make sure whatever password is used is remembered and the same as the password on the config folder under dev.exs file
    *  on the dev.exs file keep the user as 'postgres' otherwise auth might fail.
5) `\q` <br>
	* use this to quit postgres terminal and  restart postgres in the event it was started before
	
  6) `sudo systemctl restart postgresql service` <br>
  
  7) `psql -version`
  
  * check if postgres is installed will give a psql error and that is fine. <br>
	
  8) `mix local.hex`
  
  * to install Hex and update it to the latest version if it is already installed <br>

  9) `mix archive.install hex phx_new`
  
  * since we alreadyhave Elixir and Erlang installed we move directly to install  the Phoenix application generator. <br>
	
  10) `mix phx.new discuss`
	
  * start a phx project called discuss to test out postgresql and phoenix <br>
	
  11) `- y`
  
  * choose yes to install all dependancy, you can run this later if neede or dependancies need to be updated using <br>
  
  12) `mix deps.get`
  
  `https://www.postgresql.org/ftp/pgadmin/pgadmin4/v7.5/windows/` <br>
  
 * use this link and download pg4Admin on the latest version, windows os choose the exe file download and install it, we will use it to view our database <br>
	
  13) `mix ecto.create`
  
 * The database for Discuss.Repo has been created is the message you get, any other error gotten e.g auth failed error means your "config -> dev.exs" is not properly configured and make sure it is the same as the postgres credentials. <br>
  
  14) `mix phx.server`
  
 * runs the phoenix server on http://localhost:4000 you could check this on your webbrowser to confirm your Phoenix server is up and running now to confirm the database using pgAdmin <br>
   
 * run the pgAdmin as administrator 
  
 * Select on start new server
  
 * Under General,
  
   * On name set it as 'localhost'
  
 * Under Connection,
 
  * add Host name/address as 127.0.0.1 at the password space put your postgresql password that was set-up above.
  
  * save and head back to ubuntu terminal  under the discuss folder
  
  * run the following script commands to set up files on our project
  
  * with each command we need to update the route on our  discus_web
	under router.ex file 
  
  15) `mix phx.gen.html Discussions Topic topics title:string`
  
  * resources "/topics", TopicController
    
  16) `mix phx.gen.html Accounts User users email:string`
  
  * resources "/users", UserController
  
  17) `mix phx.gen.html Discussions Comment comments content:string`
  
  * resources "/comments", CommentController
  
  Now run
  
  18) `mix.ecto migrate` 
  
  * to migrate all files then restart your phoenix server
  
  19) `mix phx.server`
  
  * it should run successfully go to your webbrowser and run http://localhost:4000/topics
  
  * check if you can add, edit and remove topics 
  
  * Go to your pgAdmin and refresh your discuss_dev database
  
  * under schema you should be able to view all the tables generated and data added via the webbrowser
  
  * this confirms everything is working and in sync
  
	
