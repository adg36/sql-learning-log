# 🎬 CS50 SQL Practice – IMDB Query: Cooper & Lawrence

## Problem
From the CS50 Problem Set 7, the task was to write a SQL query to list the titles of all movies in which both Bradley Cooper and Jennifer Lawrence starred.

## My Approach
Without looking at any hints or walkthroughs, I wrote the following query:

```
SELECT title
FROM movies
JOIN stars ON stars.movie_id = movies.id
JOIN people ON people.id = stars.person_id
WHERE name = 'Bradley Cooper' OR name = 'Jennifer Lawrence'
GROUP BY title
HAVING COUNT(title) > 1;
```
This worked and passed the check. My reasoning was:

I needed only movie titles.

I knew each actor is linked to a movie through the stars table.

So I joined movies with stars, and then stars with people.

I filtered for rows where either of the two actors was present.

I grouped by title and kept only those titles that had more than one match — meaning both actors were associated with that movie.

## CS50’s Suggested Approach
Afterwards, I looked at the walkthrough, which suggests a more step-by-step algorithmic method:

1. Find Bradley Cooper’s ID.
2. Find Jennifer Lawrence’s ID.
3. Get the list of movie IDs for each.
4. Find the intersection of those movie IDs.
5. Retrieve titles for those movies.

This approach is more modular, possibly more readable and extensible, and closer to how one might build a solution incrementally when exploring an unfamiliar schema.

## Reflection
I’m glad I solved this independently and got a correct result, but it also made me reflect on algorithmic thinking vs set-based reasoning in SQL:

The suggested approach emphasizes clarity and traceability — breaking the problem into smaller queries that could be debugged or tested separately.

Although I think both are valid, I acknowledge that, in a more complex or messy real-world dataset, the step-by-step method might be more robust.

## What I Learned
Writing SQL is often like solving a puzzle — and there are multiple correct paths.

It’s worth revisiting "official" or "suggested" solutions to see different ways of thinking.

Keeping track of how I reason through problems (even if my approach isn’t the “standard” one) helps me understand both the tools and my own cognitive style.
