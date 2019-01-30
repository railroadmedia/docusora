# Brand Application URL Structures

# Logged In Areas

## Dashboard/Home Page
This is the main home page for a logged in user, they are sent here after logging in or purchasing a product.
> /members

</br></br>

## Learning Paths

This is a list of all learning paths, or a learning path catalogue.
> /members/learning-paths

</br></br>

The details page for a specific learning path, it shows all the content within the learning path.
> /members/learning-paths/{LP SLUG}/{LP ID}

</br></br>

The details page for a unit (basically a course) within the learning path, it shows a list of lessons in the unit.
> /members/learning-paths/{LP SLUG}/{LP ID}/{UNIT SLUG}/{UNIT ID}

</br></br>

* NOTE: Drumeo does not follow this structure, see drumeo learning paths at the bottom

Lesson page for the lesson in the unit in the learning path.
> /members/learning-paths/{LP SLUG}/{LP ID}/{UNIT SLUG}/{UNIT ID}/{LESSON SLUG}/{LESSON ID}


* NOTE: Drumeo does not follow this structure, see drumeo learning paths at the bottom
</br></br>

## Courses
> members/courses/

This is the courses catalogue.

This is the course overview/details page, it shows a list of lessons in the course.
> /members/courses/{COURSE SLUG}/{COURSE ID}

</br></br>

Lesson page for the lesson in the course.
> /members/courses/{COURSE SLUG}/{COURSE ID}/{LESSON SLUG}/{LESSON ID}

</br></br>

## Shows

This is an overview page with a list of all shows.
> /members/shows

</br></br>

This is the specific shows lesson catalogue.
> /members/shows/{SHOW CONTENT TYPE}

</br></br>

This is the lesson page for the lesson in the show. </br>
> /members/shows/{SHOW CONTENT TYPE}/{LESSON SLUG}/{LESSON ID}

</br></br>

## Packs

List of all the users packs.
> /members/packs

</br></br>

Overview page for the pack, it shows a list of DVDs or units.
> /members/packs/{PACK SLUG}/{PACK ID}

</br></br>

This is a pack unit (previously known as DVD) overview page, it shows a list of lessons in the unit.
> /members/packs/{PACK SLUG}/{PACK ID}/{UNIT SLUG}/{UNIT ID}

</br></br>

This is the lesson page for the lesson in the unit.
> /members/packs/{PACK SLUG}/{PACK ID}/{UNIT SLUG}/{UNIT ID}/{LESSON SLUG}/{LESSON ID}

</br></br>

## Content Types

This is the catalogue for the given content type. This should be pluralized.
> /members/{CONTENT TYPE}

</br></br>

This is the catalogue for the given content type. This should be pluralized.</br></br>
> /members/{CONTENT TYPE}
