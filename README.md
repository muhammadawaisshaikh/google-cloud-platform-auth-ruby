# google-cloud-platform-auth-ruby
google cloud platform authentication using google-api-client gem

# STEPS GET DONE

# 1. Creating and Setting Up
rails new ecommerce --api -d postgresql -T

# 2. Setting API subdomain in routes.rb
Rails.application.routes.draw do
  constraints subdomain: 'api' do
  end
end

# 3. Creating book model
rails g model User name:string mobile:string

# 4. for create the database
rake db:create

# 5. to create book table
rake db:migrate

# 6. Setting API Versioning
gem 'versionist' in GEMLFILE
RUN rails generate versionist:new_api_version v1 V1 --path=value:v1

# 7. adding api_versioning in namespace under routes.rb
api_version(:module => "V1", :path => {:value => "v1"}) do
end

# 8. for creating routes for books CRUD in routes.rb add:
resources :books

# 9. create the books controller inside version 1 - controllers/v1
rails g controller v1/users index create show update destroy

# 10. OPEN rails c
RUN User.create(name: "Awais", mobile: "+923312737076")

# 11. Now just start your rails server and go to your postman and 
GET http://localhost:4000/v1/users

# 12. Creating the others actions (Create, Show, PUT/Patch, Delete)
mentioned in app/controllers/v1/books_controller.rb
