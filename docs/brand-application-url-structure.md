# Brand Application URL Structures

# Logged In Areas

## Dashboard/Home Page
This is the main home page for a logged in user, they are sent here after logging in or purchasing a product.
> /members

## Learning Paths

This is a list of all learning paths, or a learning path catalogue.
> /members/learning-paths

The details page for a specific learning path, it shows all the content within the learning path.
> /members/learning-paths/{LP SLUG}/{LP ID}

The details page for a unit (basically a course) within the learning path, it shows a list of lessons in the unit.
> /members/learning-paths/{LP SLUG}/{LP ID}/{UNIT SLUG}/{UNIT ID}

* NOTE: Drumeo does not follow this structure, see drumeo learning paths at the bottom

Lesson page for the lesson in the unit in the learning path.
> /members/learning-paths/{LP SLUG}/{LP ID}/{UNIT SLUG}/{UNIT ID}/{LESSON SLUG}/{LESSON ID}


* NOTE: Drumeo does not follow this structure, see drumeo learning paths at the botto

## Courses
> members/courses/

This is the courses catalogue.

This is the course overview/details page, it shows a list of lessons in the course.
> /members/courses/{COURSE SLUG}/{COURSE ID}

Lesson page for the lesson in the course.
> /members/courses/{COURSE SLUG}/{COURSE ID}/{LESSON SLUG}/{LESSON ID}

## Shows

This is an overview page with a list of all shows.
> /members/shows

This is the specific shows lesson catalogue.
> /members/shows/{SHOW CONTENT TYPE}

This is the lesson page for the lesson in the show. </br>
> /members/shows/{SHOW CONTENT TYPE}/{LESSON SLUG}/{LESSON ID}

## Packs

List of all the users packs.
> /members/packs

Overview page for the pack, it shows a list of DVDs or units.
> /members/packs/{PACK SLUG}/{PACK ID}

This is a pack unit (previously known as DVD) overview page, it shows a list of lessons in the unit.
> /members/packs/{PACK SLUG}/{PACK ID}/{UNIT SLUG}/{UNIT ID}

This is the lesson page for the lesson in the unit.
> /members/packs/{PACK SLUG}/{PACK ID}/{UNIT SLUG}/{UNIT ID}/{LESSON SLUG}/{LESSON ID}

## Content Types

This is the catalogue for the given content type. This should be pluralized.
> /members/{CONTENT TYPE}

This is the catalogue for the given content type. This should be pluralize
> /members/{CONTENT TYPE}
