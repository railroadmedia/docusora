# Brand Application URL Structures

# Logged In Areas


## Dashboard/Home Page

This is the main home page for a logged in user, they are sent here after logging in or purchasing a product.
> /members


## Learning Paths

This is a list of all learning paths, or a learning path catalogue.
> /members/learning-paths

</br>

The details page for a specific learning path, it shows all the content within the learning path.
> /members/learning-paths/ **{LP SLUG}** / **{LP ID}** 

</br>

The details page for a unit (basically a course) within the learning path, it shows a list of lessons in the unit.
> /members/learning-paths/ **{LP SLUG}** / **{LP ID}** / **{UNIT SLUG}** / **{UNIT ID}** 

</br>

Lesson page for the lesson in the unit in the learning path.
> /members/learning-paths/ **{LP SLUG}** / **{LP ID}** / **{UNIT SLUG}** / **{UNIT ID}** / **{LESSON SLUG}** / **{LESSON ID}** 


## Courses

This is the courses catalogue.
> members/courses/

</br>

This is the course overview/details page, it shows a list of lessons in the course.
> /members/courses/ **{COURSE SLUG}** / **{COURSE ID}** 

</br>

Lesson page for the lesson in the course.
> /members/courses/ **{COURSE SLUG}** / **{COURSE ID}** / **{LESSON SLUG}** / **{LESSON ID}** 


## Shows

This is an overview page with a list of all shows.
> /members/shows

</br>

This is the specific shows lesson catalogue.
> /members/shows/ **{SHOW CONTENT TYPE}** 

</br>

This is the lesson page for the lesson in the show. </br>
> /members/shows/ **{SHOW CONTENT TYPE}** / **{LESSON SLUG}** / **{LESSON ID}** 


## Packs

List of all the users packs.
> /members/packs

</br>

Overview page for the pack, it shows a list of DVDs or units.
> /members/packs/ **{PACK SLUG}** / **{PACK ID}** 

</br>

This is a pack unit (previously known as DVD) overview page, it shows a list of lessons in the unit.
> /members/packs/ **{PACK SLUG}** / **{PACK ID}** / **{UNIT SLUG}** / **{UNIT ID}** 

</br>

This is the lesson page for the lesson in the unit.
> /members/packs/ **{PACK SLUG}** / **{PACK ID}** / **{UNIT SLUG}** / **{UNIT ID}** / **{LESSON SLUG}** / **{LESSON ID}** 


## Content Types

This is the catalogue for the given content type. This should be pluralized.
> /members/ **{CONTENT TYPE}** 

</br>

This is the lesson page for a content types lesson if it does not have children.
> /members/ **{CONTENT TYPE}** / **{LESSON SLUG}** / **{LESSON ID}** 

</br>

This is the overview page for the singular content type if it has children.
> /members/ **{CONTENT TYPE}** / **{PARENT SLUG}** / **{PARENT ID}** / **{LESSON SLUG}** / **{LESSON ID}** 


## Live & Schedule

This is the live page which shows the schedule if nothing is live at the current time.
> /members/live

</br>

This is the schedule page, a list of upcoming live events and content releases
> /members/schedule

</br>
