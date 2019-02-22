# Infrastructure Proposal

## Portal
* Student access & instructor access
* Check assignments delivered/skipped \[instructor/student\]
* Check future events \[instructor/student\]
* Register assignment (learning unit) and repo (inst and student) \[instructor\]
* Keep track of assignment versions
    - Instructors tag (on GitHub) releasable versions
    - New release adds new version to grader
    - New release updates student repo with correct tag
* Submit assignment \[student\]
    - Assignment submission fires grading
    - Forbid uploading of old assignment versions
    - Student file is copied to correct structure as expected by grader 
    (ex: submission/<student_id>/lu01-v1.1/)
    - Grades are shown by directly querying grader DB (?)

### Hackathon
* Check hackathons attended/skipped \[instructor/student\]
* Register hackathon \[instructor\]
* Register hackathon attendance \[student\]
* Create hackathon teams \[instructor\]
* Set hackathon image link and team name \[student\]
* Run hackathon leaderboard

## Grader
* Grader keeps all versions of an assignment (ex: lu01-v1.1)
* GitHub webhook to push updates to assignments (tag to release ex: v1.0)
* Use the assignment environment to run the notebooks (how to do this?)

