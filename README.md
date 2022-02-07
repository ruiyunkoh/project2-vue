# SHARE AND SHED

By: <b>Koh Rui Yun</b>

# 1. Project Summary
The project aims to build a website as a sharing platform for like-minded fitness community to share exercise routine that works, with others who are interested. 
This is especially so in this period of pandemic, whereby the website can promote and share fitness routine easily without the necessity of heading to a gym. 

Owner goal: To promote health and fitness through encouraging sharing of routine online. <br>
User goal: To find exercise routine that fits their criteria (which they can filter), and even share any other routine that works for them within the platform. 

  ### Relevant website links
  a. Website deployment on Netlify: https://practical-galileo-4a477c.netlify.app <br>
  b. Github Repository for Express and mongodb for backend: https://github.com/ruiyunkoh/project2-mongo <br>
  c. API deployed on Heroku: https://kry-exercise.herokuapp.com/find_exercise

# 2. UIUX / Features

 ## 2.1 UIUX
 
  ### 2.1.1 Identifying user stories
  a. As a user, I want to view all exercise routine that meets my criteria (type, intensity, target area). <br>
  b. As a user, I would like to share exercise routine that had worked for myself. <br> 
  
  ### 2.1.2 Acceptance criteria
  a. The website allows user to post their own exercise routine. <br>
  b. The website allows filtering of posts (by users) based on filter criteria (type, intensity, target area) <br>
  c. The website ensures that all creation/updating of forms has every field filled in before submission - such that relevant search fields are filled for categorisation. 
 
  ### 2.1.3 Wireframe and Five Planes of UI/UX
  The main feature of the front-end application of this project is the 'Exercise' page that displays all exercise postings. 
  
  <li> Surface: The visual design of the Home page (the page which users first see when they enter website) displays an attention grabbing banner that take up the full view size. <br>
The whole website features muted colours, with a slight darker undertone. The colour scheme conveys simplicity and its darker undertone gives a hint of motivation and power to users. Colours were well chosen to ensure readability and colours are not clashing to cause mental stress.</li>
  <li> Skeleton: For ease of navigating through the webpage, the Navbar being used as the main navigator. </li>
  <li> Structure: Each posting is contained within a card format. Within each card shows user a brief content summary of the exercise. They are able to click to view more. </li>
  
  A rough sketch for the layout of the website was done during the planning stage. Subsequently, changes were slowly made to eventually evolve into the current website. <br>
  You may find the planning stage wireframe here: [wireframe pdf] (/uiux-files)
  
  ### Exercise page 
 
 ## 2.2 Features
 
 *Note: If results do not show on the 'Exercise' page on loading, kindly click refresh. 
 
# 3. Implementation

 ## 3.1 Technology used
 
 ## 3.2 Testing
 
# 4. Deployment
  
  <li> The project was built on Gitpod, and monitored via port 8000 after enabling yarn serve, before being deployed on Netlify. </li>
  <li> The project was committed, staged, and pushed to GitHub on a usual basis. </li>
  <li> MongoDB database was built using Mongo Atlas. Backend utilises express as its web application framework and connects to MongoDB. Backend is deployed to Heroku. </li>
  
  ### Front-end using Vue
  All codes can be found with 'src' folder. <br>
  Images used are within the 'assets' folder, while the various components of the website are within the 'components' folder. <br>
  Files not relevant to be published to github, are included in gitignore folder. <br>
  
  ### Back-end using Express and MongoDB
  All codes are done in 'index.js' and 'MongoUtil.js'. <br>
  Files not relevant to be published to github, are included in gitignore folder. <br>


# 5. Credits

 ## Content - Fitness routine
 <li> nerdfitness.com/blog/beginner-body-weight-workout-burn-fat-build-muscle/ </li>
 <li> https://www.menshealth.com/fitness/a25424850/best-hiit-exercises-workout/ </li>
 <li> https://www.medicalnewstoday.com/articles/cardio-exercises-at-home#advanced-exercises </li>
 <li> https://www.youtube.com/watch?v=WGnCC4udvlw </li>
 <li> https://www.tummee.com/yoga-sequences/arm-balance-sequence-for-gaining-strength-in-arms </li>
 <li> https://www.bupa.co.uk/newsroom/ourviews/waking-up-stretching </li>
 <li> https://www.youtube.com/watch?v=yU5uWAMed7k </li>
 <li> https://www.verywellfit.com/advanced-ab-workout-3120074 </li>
 
 ## Image
 <li> Banner photo: https://www.gu.se/en/news/anxiety-effectively-treated-with-exercise </li>
 
