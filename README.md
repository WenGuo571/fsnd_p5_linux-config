## Conference Central - FSND P5
### Poject Description:
Cloud-based API server to support a conference organization application.
### What's included
catalog/   
|--- client_secrets.json          
|--- database_setup.json           
|--- demo_items.json           
|--- project.py                
|--- static/              
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- bootstrap/         
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- fonts/             
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- img/       
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- js/        
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- app.js           
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- controllers.js           
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- partials/              
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- conference_detail.html 	
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- create_conferences.html             
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- home.html           
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- login.modal.html              
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- profile.html           
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- show_conferences.html           
|--- templates/             
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--- index.html                      

### Live Demo
APIs: https://conference-central-1159.appspot.com/_ah/api/explorer              
Application: https://conference-central-1159.appspot.com    
### Running locally
1. create project and project credentials in https://console.developers.google.com/project
2. clone project
3. update personal project information:             
    (1) app.yaml: application         
    (2) settings.py: client_id              
    (3) /static/js/app.js: client_id
4. install Google App Engine Launcher from https://cloud.google.com/appengine/downloads?hl=en              
5. add project to app engine launcher and add local address to google projects credentials (eg. port: 5000)             
6. start app engine
7. access and test application: 'http://localhost:5000'
8. access and test application APIs: 'http://localhost:5000/_ah/api/explorer'
9. stop

### Design Explaination
1. __Task 1__:              
__sessions__:               
session belongs to conference, so sesssions are created with one conference object as their parent. This attribution gives sessions a natural group that belongs to same conference.                 
__speaker__:                            
Instead create speaker entity in database, I simply list spaker as an attribution of session. All information about speaker is speaker's name and if this speaker is featured speaker or not. We could simply query sessions to figure out if this speaker is featured or not. So, I think this solution is efficient.
2. __Task 3__:              
__filterSession__ -- filter sesssions with latest start time and topics that are should be ignored.                      
__getSesssionsWithHighlight__ -- figure out sessions with specific highlights array. Highlighs of each session is sorted for easier filter.              

### Result
All tests passed!

### Creator
WEN GUO
