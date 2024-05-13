# Postmortem

![Oppps!!!](postmortem.JPG)

## Issue Summary
On May 12, 2024, shortly after deploying a new feature to our Ruby on Rails platform, we were inundated with user complaints. Within minutes of the update, our inbox was flooded with emails from frustrated users unable to sign in or sign up. The sudden influx of 127 such messages caught us off guard. Recognizing the criticality of user experience in retaining our audience, we immediately delved into the issue.

Upon cloning our site's repository and attempting to reproduce the problem, we discovered that the site failed to start up altogether. It quickly became apparent that the root cause lay in our failure to update project requirements. From 9:55 AM GMT+1 to 11:20 AM GMT+1, our platform was rendered inaccessible.


## Timeline

+ 05-12-2024, 9:55 AM GMT+1: Initial customer complaint regarding sign-in issues.
+ 05-12-2024, 10:20 AM GMT+1: Backend developer Winus experienced the same issue.
+ 05-12-2024, 10:35 AM GMT+1: Investigation into controller and view inconsistencies commenced.
+ 05-12-2024, 10:40 AM GMT+1: Suspicions arose around the bcrypt gem, a site dependency.
+ 05-12-2024, 10:42 AM GMT+1: Verification of form field bindings in views.
+ 05-12-2024, 10:45 AM GMT+1: Controller hash generation under scrutiny.
+ 05-12-2024, 10:50 AM GMT+1: Speculation on password hashing accuracy.
+ 05-12-2024, 11:00 AM GMT+1: Incident escalated to the backend development team.
+ 05-12-2024, 11:20 AM GMT+1: Resolution through bcrypt gem version update.

## Root Cause And Resolution

The outdated version of the bcrypt gem was incompatible with the hash generation, causing authentication failures despite valid hashes. Backend developer Winus swiftly rectified the issue by updating the Gemfile.lock to a more recent bcrypt version and reinstalling necessary gems, restoring functionality seamlessly.

## Corrective And Preventative Measures

Continuous Integration Pipeline: Implementation of a CI pipeline to validate pull request branches before merging, ensuring build stability.
Monitoring System: Establishment of robust monitoring for both database and application servers to detect and address issues promptly.
Test Development: Enforcing rigorous testing protocols for new features, mandating passage before integration to the deployment branch to forestall future disruptions.