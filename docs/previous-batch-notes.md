Notes from Previous Batch
=================

## Local Setups
There are many subtle differences between package versions and even builds
of the same package and system libraries.
To minimize problems that come up from this we need to create setup guides
both for students and instructors.

For students we can use the existing 
[setup guide](https://github.com/LDSSA/setup).
Except that there should be a setup per assignment to avoid clashes
between assignments created by different instructors.

Instructors should have instructions of how to create an initial environment 
and a writen guide of how to freeze the environment once the assignment is 
writen.
This environment spec will be delivered to the students allowing them to work
with as close as possible the same environment as the instructor.

Last year there was some problems of package name differences between
packages names available for different systems (Windows vs Mac/Linux).
We'll need someway to check this and a process in place to deal with it.

## Management Portals
Last year we had three user facing interfaces: GitHub, JupyterHub (Grader) 
and The Portal (as himself).

### Portal
Last years portal was done in Laravel, if there are no members in the infra
team with experience in PHP this should probably be changed.

### GitHub
GitHub was used for instructor assignment submission and delivery to students.
Per assignment two repositories where created, one with the instructors version
(with the assignment solution) and another with the students version.
Using GitHub has the advantage of having a ticketing system included and
giving a well defined, know interface to make changes to the assignment.
I would argue that these pros justify keeping GitHub.

Once an instructor was done with an assessment (and whenever he made changes)
he would have to as the infrastructure team to deploy the changes to the
student version.
Initially this step was done by the instructor by later was changed to allow
the infra team to create the student version (the solutions for the assignment
where removed by the grader component) and to review changes and install
packages in the grader component.
This process is labour intensive and should probably be improved upon.

Also steps must be taken to ensure all interested parties are watching the
correct repositories i.e. instructors the repo where students will open 
tickets.
There's the additional problem that by default closed tickets don't show up,
we need to make clear to students that they should look at closed tickets
too.

As a delivery system for students it works fine.
But there needs to be an easier way of merging the student's changes with
any updates they pull from the repo.
And this needs to be documented.
I experimented with this idea in the repo `nbgrader_merge` but never finished
it.
Also maybe tools like [nbdime](https://github.com/jupyter/nbdime) already
solve this problem.

## Grader
We used an instance of JupyterHub+Nbgrader to do grading and manage 
assignments (the grader part).
The infra team would create the assignment on grader and then copy
the student version to the student repository.
Students delivered the exercise via the portal which would place the file
in a shared directory.
The grader periodically extracts the files to the location the grader expects
it and runs the grading on it.
Another periodic task would retrieve the grade and place it in the portal's
database.
This process suffered from some sync problems.

NbGrader is cool, but there were several limitations/problems during the last
edition.
* Low student visibility of results
* Hard to release bugfixes
* Hard to have different environments for each assignment
* Split between grader and portal databases

### Low Visibility
By not allowing hidden tests for example the student visibility problem is 
moot.

### Bugfixes
Releasing fixes would require a deeper understanding of when does nbgrader
"lock" an assignment, this was never well understood.
Also there are questions of how to deal with different versions of an 
assignment.
If a student delivers an "old" assignment should it be graded against the old
version or refused?
If a new version is released what should we do to the current grades?

## Hackathons
Hackathon attendance and leaderboard could easily be automated.
It involved creating a new site for the leaderboard (with a new grading fcn)
and a lot of copy pasting for teams.
If students mark their presence on the portal team creation can be automated.
Remember the remote students though.

## Academy Artifacts
Currently the previous academy artifacts are split in stopped machines, 
stopped db's and s3 buckets.
We need a proposal for storing the artifacts we need to kee and place
them in storage.
