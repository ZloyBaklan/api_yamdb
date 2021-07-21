# YaMDb Project
The YaMDb Project collects User Reviews for Titles. The works are divided into categories: "Books", "Films", "Music". The list of categories (Category) can be expanded (for example, you can add a category "Fine Arts" or "Jewelry").
The works themselves are not stored in YaMDb, you cannot watch a movie or listen to music here.
Each category contains works: books, films or music. For example, the “Books” category may include the works “Winnie the Pooh and All, All, All” and “The Martian Chronicles”, and in the “Music” category - the song “Now” by the group “Insects” and the second Bach suite. A work can be assigned a genre (Genre) from the list of preset ones (for example, "Fairy Tale", "Rock" or "Arthouse"). New genres can only be created by the administrator.
Grateful or outraged readers leave text reviews for the works (Review) and give the work a rating (an estimate in the range from one to ten). The average score of the product is calculated from the set of ratings.

# Custom Roles
Anonymous - can view descriptions of works, read reviews and comments.
Authenticated user (user) - can read everything, like Anonymous, can additionally publish reviews and rate works (films / books / songs), can comment on other people's reviews and rate them; can edit and delete their reviews and comments.
Moderator - the same rights as the Authenticated User plus the right to delete and edit any reviews and comments.
Administrator (admin) - full rights to manage the project and all its contents. Can create and delete works, categories and genres. Can assign roles to users.
Django Administrator - The same rights as the Administrator role.

# YaMDb API Resources
AUTH resource: authentication.
USERS resource: users.
Resource TITLES: works to which reviews are written (a specific film, book or song).
Resource CATEGORIES: categories (types) of works ("Films", "Books", "Music").
Resource GENRES: genres of works. One work can be linked to several genres.
Resource REVIEWS: reviews of works. The review is tied to a specific work.
COMMENTS resource: Comments on reviews. The comment is linked to a specific review.
Each resource is described in the documentation: endpoints (addresses at which a request can be made), allowed types of requests, access rights and additional parameters, if necessary, are indicated.

# Linked data and cascading deletion
Deleting a User object should remove all of that user's reviews and comments (along with ratings).
When deleting the object of a work Title, all reviews for this work and comments to them must be deleted.
When deleting an object of a Category, do not delete the works associated with this category (Title).
When deleting a Genre object, do not delete the titles associated with that genre (Title).
When you delete a Review review object, all comments on that review must be deleted.
