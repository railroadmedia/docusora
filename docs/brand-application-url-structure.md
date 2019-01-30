# Brand Application URL Structures

# Logged In Areas

## Dashboard/Home Page
> /members

This is the main home page for a logged in user, they are sent here after logging in or purchasing a product.
</br></br>

## Learning Paths

> /members/learning-paths

This is a list of all learning paths, or a learning path catalogue.
</br></br>

> /members/learning-paths/{LP SLUG}/{LP ID}

The details page for a specific learning path, it shows all the content within the learning path.
</br></br>

> /members/learning-paths/{LP SLUG}/{LP ID}/{UNIT SLUG}/{UNIT ID}

The details page for a unit (basically a course) within the learning path, it shows a list of lessons in the unit.
</br></br>

* NOTE: Drumeo does not follow this structure, see drumeo learning paths at the bottom

> /members/learning-paths/{LP SLUG}/{LP ID}/{UNIT SLUG}/{UNIT ID}/{LESSON SLUG}/{LESSON ID}

Lesson page for the lesson in the unit in the learning path.

* NOTE: Drumeo does not follow this structure, see drumeo learning paths at the bottom
</br></br>

## Courses
> members/courses/

This is the courses catalogue.

> /members/courses/{COURSE SLUG}/{COURSE ID}

This is the course overview/details page, it shows a list of lessons in the course.
</br></br>

> /members/courses/{COURSE SLUG}/{COURSE ID}/{LESSON SLUG}/{LESSON ID}

Lesson page for the lesson in the course.
</br></br>

## Shows

> /members/shows

This is an overview page with a list of all shows.
</br></br>

> /members/shows/{SHOW CONTENT TYPE}

This is the specific shows lesson catalogue.
</br></br>

> /members/shows/{SHOW CONTENT TYPE}/{LESSON SLUG}/{LESSON ID}

This is the lesson page for the lesson in the show. </br>
</br></br>

## Packs

> /members/packs

List of all the users packs.
</br></br>

> /members/packs/{PACK SLUG}/{PACK ID}

Overview page for the pack, it shows a list of DVDs or units.
</br></br>

> /members/packs/{PACK SLUG}/{PACK ID}/{UNIT SLUG}/{UNIT ID}

This is a pack unit (previously known as DVD) overview page, it shows a list of lessons in the unit.
</br></br>

> /members/packs/{PACK SLUG}/{PACK ID}/{UNIT SLUG}/{UNIT ID}/{LESSON SLUG}/{LESSON ID}

This is the lesson page for the lesson in the unit.
</br></br>

## Content Types

> /members/{CONTENT TYPE}

This is the catalogue for the given content type. This should be pluralized.
</br></br>

> /members/{CONTENT TYPE}

This is the catalogue for the given content type. This should be pluralized.</br></br>