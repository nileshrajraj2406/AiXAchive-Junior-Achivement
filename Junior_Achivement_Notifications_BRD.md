**Notification Management System BRD**

**Flow of Notifications triggered and receive and tracking**

**1. Overview**

The Notification Management System shall manage automated email communication throughout the **AiXAchieve 5Y Application Lifecycle**.

The system shall ensure that applicants receive timely, accurate, and lifecycle-based communication during each stage of their application journey, including:

- Application submission confirmation;

- Application review outcome;

- Virtual interview invitation;

- Interview reminders;

- Interview confirmation;

- Interview evaluation outcome;

- In-person interview invitation;

- Final decision communication;

- Acceptance confirmation;

- Offer decline communication;

- Next-step communication.

The notification system shall be triggered based on applicant lifecycle state changes and configured business rules.

**2. Notification Lifecycle Flow**

flowchart TD

A\[Application Submitted\]

A --\> B\[Application Received Email\]

B --\> C{Application Review}

C --\>\|Not Eligible\| D\[Application Rejection Email\]

C --\>\|Eligible\| E\[Virtual Interview Invitation\]

E --\> F{Interview Scheduled}

F --\>\|No Response\| G\[Virtual Interview Reminder 1\]

G --\> H\[Virtual Interview Reminder 2\]

F --\>\|Scheduled\| I\[Virtual Interview Confirmation\]

I --\> J\[Virtual Interview Evaluation\]

J --\>\|Rejected\| K\[Virtual Interview Rejection Email\]

J --\>\|Selected\| L\[In-Person Interview Invitation\]

L --\> M{RSVP Completed}

M --\>\|No Response\| N\[In-Person Reminder 1\]

N --\> O\[In-Person Reminder 2\]

M --\>\|Confirmed\| P\[In-Person Interview Confirmation\]

P --\> Q\[Final Evaluation\]

Q --\>\|Rejected\| R\[Final Rejection Email\]

Q --\>\|Accepted\| S\[Acceptance Email\]

S --\> T{Applicant Response}

T --\>\|Declined\| U\[Good Luck Email\]

T --\>\|Accepted\| V\[Next Steps Email\]

**3. Notification Trigger Matrix**

| **Notification ID** | **Application State**          | **Email Purpose**        | **Trigger Timing**           |
|---------------------|--------------------------------|--------------------------|------------------------------|
| NT-001              | Application Received           | Confirm submission       | Immediately after submission |
| NT-002              | Application Denied             | Inform rejection         | After application review     |
| NT-003              | Virtual Interview Invitation   | Invite applicant         | After application approval   |
| NT-004              | Virtual Interview Reminder 1   | Follow-up scheduling     | 3 days after invitation      |
| NT-005              | Virtual Interview Reminder 2   | Final reminder           | 1 week after reminder 1      |
| NT-006              | Virtual Interview Confirmation | Confirm interview        | After scheduling             |
| NT-007              | Virtual Interview Rejection    | Inform rejection         | After virtual evaluation     |
| NT-008              | In-Person Interview Invitation | Invite final interview   | After virtual approval       |
| NT-009              | In-Person Reminder 1           | RSVP reminder            | 3 days after invitation      |
| NT-010              | In-Person Reminder 2           | Final RSVP reminder      | 1 week after reminder 1      |
| NT-011              | In-Person Confirmation         | Confirm attendance       | After RSVP                   |
| NT-012              | Final Rejection                | Inform final rejection   | After final evaluation       |
| NT-013              | Acceptance                     | Welcome applicant        | After acceptance decision    |
| NT-014              | Offer Declined                 | Thank applicant          | After decline                |
| NT-015              | Next Steps                     | Share onboarding details | After acceptance             |

**4. Email Template Specifications**

**NT-001: Application Received Confirmation**

**Trigger State**

**Application Received**

**When To Send**

Immediately after successful application submission.

**Recipient**

Student Applicant

**Subject**

**We Received Your 5th Year Application! 🎉**

Subject: We Received Your 5th Year Application! 🎉 

Hi \[First Name\], 

Thank you for applying to 5th Year by Junior Achievement! We’re excited that you’re interested in taking this next step toward building your future. 

Your application has been successfully received and will now be reviewed by the 5th Year team. 

We’ll be in touch with you about the next steps in the application process. In the meantime, keep an eye on your inbox for updates from the 5th Year Team. 

Good luck and thank you for taking the time to apply! 

**Static Content**

Thank you for applying to 5th Year by Junior Achievement.

Your application has been successfully received and will now be reviewed by the 5th Year team.

We’ll be in touch with you about the next steps in the application process.

**Dynamic Content**

| **Field**       | **Description**       | **Source**         |
|-----------------|-----------------------|--------------------|
| First Name      | Applicant greeting    | Applicant Profile  |
| Application ID  | Tracking reference    | Application System |
| Submission Date | Application timestamp | Application Record |

**NT-002: Application Rejection Email**

**Trigger State**

Application Review Completed → Not Eligible

**When To Send**

After application review.

**Eligibility Failure Conditions**

Applicant does not satisfy:

- Must be 18 years old by August 15, 2027.

- Must have work experience or extracurricular involvement.

**Subject**

**An Update on Your 5th Year Application**

Subject: An Update on Your 5th Year Application 

 

Hi \[First Name\], 

Thank you for your interest in 5th Year and for taking the time to submit your application. 

After reviewing your application, we’re sorry to share that you are not eligible to move forward in the 5th Year application process at this time. 

Based on the information provided in your application, you do not currently meet one or more of these eligibility requirements. 

- Being 18 years old by August 15, 2027 

<!-- -->

- Having prior work experience or extracurricular involvement 

This does not mean that you can’t apply again in the future! We encourage you to continue gaining experience through employment, extracurricular activities, volunteering, and other opportunities that allow you to build your skills and explore your interests. 

Thank you again for considering 5th Year as part of your journey. We wish you all the best as you prepare for what comes next! 

**Static Content**

Thank you for your interest in 5th Year.

After reviewing your application, we’re sorry to share that you are not eligible to move forward.

We encourage you to continue building your skills and exploring future opportunities.

**Dynamic Content**

| **Field**        | **Source**             |
|------------------|------------------------|
| First Name       | Applicant Profile      |
| Rejection Reason | Eligibility Evaluation |
| Failed Criteria  | Review Result          |

**NT-003: Virtual Interview Invitation**

**Trigger State**

Application Approved

**When To Send**

When student advances past application review.

**Subject**

**5th Year Application Update – Let’s connect! 🎉**

Hi \[First Name\], 

Great news! You’ve been selected to move forward in the 5th Year application process. 

Your next step is a virtual group interview with the 5th Year Team. 

During the interview, you’ll have the opportunity to meet other applicants, learn more about the program, and tell us more about yourself, your interests, and your goals. 

Your Next Step: 

Please use the link below to select a virtual interview time: 

👉 \[SCHEDULE YOUR INTERVIEW\] 

Please select your interview time as soon as possible. Your interview is an important part of the selection process. 

We’re excited to meet you! 

**Static Content**

Great news! You’ve been selected to move forward in the 5th Year application process.

Your next step is a virtual group interview with the 5th Year Team.

**Dynamic Content**

| **Field**                   | **Source**         |
|-----------------------------|--------------------|
| First Name                  | Applicant Profile  |
| Interview Registration Link | Scheduling Module  |
| Available Slots             | Interview Calendar |

**NT-004: Virtual Interview Reminder 1**

**Trigger**

Invitation sent but interview not scheduled.

**Timing**

3 days after virtual interview invitation.

Subject: Reminder: Schedule Your 5th Year Interview 

 

Hi \[First Name\], 

We wanted to send you a quick reminder that you’ve been invited to participate in a 5th Year virtual group interview, but we don’t see an interview time scheduled for you yet. 

We’d love to meet you and learn more about you! 

👉 \[SCHEDULE YOUR INTERVIEW\] 

Please select a time as soon as possible so we can reserve your spot. 

If you have any questions or are having trouble scheduling, please reach out to the 5th Year Team at <u>my5thyear@ja.org</u> 

We hope we get the chance to e-meet you! 

**Dynamic Fields**

| **Field**                 |
|---------------------------|
| First Name                |
| Interview Scheduling Link |
| Support Email             |

**NT-005: Virtual Interview Reminder 2**

**Trigger**

Still not scheduled.

**Timing**

1 week after first reminder.

Subject: Final Reminder: Schedule Your 5th Year Interview 

 

Hi \[First Name\], 

This is a final reminder that you’ve been invited to participate in a 5th Year Virtual Group Interview, but we still don’t have an interview time scheduled for you. 

If you’re still interested in moving forward, please schedule your interview using the link below: 

👉 \[SCHEDULE YOUR INTERVIEW\] 

If you have questions or need assistance scheduling, please contact us at my5thyear.org. 

We hope to hear from you! 

**Dynamic Fields**

| **Field**             |
|-----------------------|
| First Name            |
| Final Scheduling Link |
| Contact Information   |

**NT-006: Virtual Interview Confirmation**

**Trigger**

Applicant schedules interview.

**Timing**

Once student schedules interview.

**Subject**

You're Scheduled! Your 5th Year Virtual Interview Details

Subject: You're Scheduled! Your 5th Year Virtual Interview Details 

 

Hi \[First Name\], 

You’re officially scheduled for your 5th Year Virtual Group Interview! 

We’re looking forward to connecting with you and learning more about you. 

 

**<u>Your Interview Details:</u>** 

Date: \[DATE\] 

Time: \[TIME\] 

Location: Virtual 

Join Link: \[LINK\] 

 

**<u>What to Expect:</u>** 

Your virtual group interview is a chance for us to get to know you beyond your application. You may be asked questions about your interests, experiences, goals, and why you’re interested in 5<sup>th</sup> Year! 

 

**<u>A few tips:</u>** 

- Join a few minutes early! 

<!-- -->

- Find a quiet space where you can participate without distractions. 

<!-- -->

- Make sure your camera and microphone are working. 

<!-- -->

- Come prepared to be yourself and share your experiences! 

<!-- -->

- *If for some reason you are no longer able to join the call, please inform us as soon as possible!* 

 

We’re excited to e-meet you! 

**Dynamic Fields**

| **Field**      | **Source**     |
|----------------|----------------|
| First Name     | Applicant      |
| Interview Date | Scheduler      |
| Interview Time | Scheduler      |
| Location       | Interview Type |
| Join Link      | Meeting System |

The document specifies Date, Time, Location and Join Link as interview details.

**NT-007: Virtual Interview Rejection**

**Trigger**

Virtual Interview Evaluation Failed

**When**

After virtual interview evaluation.

**Subject:** An Update on Your 5th Year Application 

 

Hi \[First Name\], 

Thank you again for participating in the **5th Year Virtual Group Interview**. 

After careful consideration, we’re sorry to share that you have not been selected to move forward to the next stage of the 5th Year application process. 

We appreciate the time and effort you put into your application and interview, and we’re grateful for your interest in 5th Year. 

We encourage you to continue exploring opportunities that help you build your professional and personal skills, gain professional experience, and prepare for your next steps. 

We wish you the very best in your future endeavors! 

**Dynamic Fields**

- First Name

- Interview Result

- Decision Status

**NT-008: In-Person Interview Invitation**

**Trigger**

Virtual Interview Passed

**When**

Student advances to in-person interview.

Subject: 5<sup>th</sup> Year Application Update - You're Moving Forward!  

 

Hi \[First Name\], 

Congratulations! You’ve been selected to move forward to the final stage of the 5th Year application process. 

Your final step is to attend our 5<sup>th</sup> Year Interview Night (In-Person). 

This interview is an opportunity for us to learn more about you, you and your parent/guardian to learn more about 5<sup>th</sup> Year, connect with current/past 5<sup>th</sup> Year Trailblazers, and some of our business partners! 

à Please \[RSVP HERE\] to let us know you are able to attend our 5<sup>th</sup> Year Interview Night (In-Person) on \[INTERVIEW DATE/TIME\] 

*\*if you are unable to attend that evening please contact us as soon as possible so we can make different arrangements\** 

 

**<u>Come Ready: </u>** 

- **Submit or Bring:** (These may be emailed to my5thyear.org prior to interview night, or brought the evening of) 

<!-- -->

- **Two letters of recommendation** written on your behalf – These must be from non-family members *(ex. Teachers, coaches, mentors, etc.)* 

<!-- -->

- Your high school **attendance records** *(we do not need your grades!)* 

<!-- -->

- *Please note: These documents are REQUIRED to be considered for the 5<sup>th</sup> Year Program. Failure to provide these documents before or at interview night may result in you no longer being considered for the program.* 

<!-- -->

- **Parent/Guardian(s):** Are **<u>required</u>** to attend. Parents/guardians will participate in a Q&A session to learn more about the 5<sup>th</sup> Year Program! 

<!-- -->

- **Prepare:** 

<!-- -->

- Come with questions to determine if the 5<sup>th</sup> Year Program is right for you 

<!-- -->

- **Business Casual** attire is required  

- Check your calendar invite for directions and parking details 

We’re excited to meet you in person! 

**Dynamic Fields**

- First Name

- Interview Date

- Interview Time

- RSVP Link

**NT-009 / NT-010**

**In-Person Interview Reminders**

**Trigger**

Invitation sent but RSVP not completed.

**Schedule**

- Reminder 1: 3 days after invitation.

- Reminder 2: 1 week after reminder 1.

- Subject: Reminder: RSVP for our 5<sup>th</sup> Year Interview Night 

 

Hi \[First Name\], 

Just a quick reminder that you’ve been invited to attend our 5<sup>th</sup> Year Interview Night (In-Person), but we don’t see an interview time scheduled for you yet. 

> If you’re interested in continuing in the application process, please RSVP below: 

👉 \[CLICK HERE TO RSVP FOR 5<sup>TH</sup> YEAR INTERVIEW NIGHT\] 

If you have questions or need help scheduling, please contact us at my5thyear.org 

We hope to see you soon! 

**Dynamic Fields**

- First Name

- RSVP Link

- Contact Details

**NT-011: In-Person Interview Confirmation**

**Trigger**

Applicant registers.

**Timing**

Once student schedules.

**Subject:**  
Your 5th Year Interview Is Confirmed, \[First Name\]! 🎉

Hi \[First Name\],

Thank you for scheduling your in-person interview for the 5th Year program! 🎉

Your interview has been successfully confirmed. We’re excited to meet you and learn more about your goals, experiences, and what you hope to achieve through the 5th Year journey.

**Your Interview Details:**

👉 **Date:** \[Interview Date\]  
👉 **Time:** \[Interview Time\]  
👉 **Location:** \[Interview Location\]

Please arrive a few minutes early and come prepared to share your experiences, interests, and what makes you excited about joining the 5th Year program.

We look forward to meeting you soon and learning more about you!

If you have any questions or need to update your interview details, please contact us at 419-865-5511 or <my5thyear@ja.org>.

See you soon! 🎉

**Dynamic Fields**

| **Field**  |
|------------|
| First Name |
| Date       |
| Time       |
| Location   |
| Address    |

**NT-012: Final Rejection**

**Trigger**

Final Interview Evaluation Failed

**Timing**

After final interview evaluation.

Hi \[First Name\], 

Thank you for participating in the 5th Year application and interview process. 

We appreciate the time, effort, and enthusiasm you brought each step of the way. 

After careful consideration of your application, interview, and supporting materials, we’re sorry to share that you have not been selected for the 5th Year program. 

Please know that we appreciate your interest in 5th Year and we encourage you to continue pursuing experiences that help you explore your interests, build your skills, and prepare for your future. 

We’re cheering you on and wishing you all the best in your next chapter! 

**Dynamic Fields**

- First Name

- Final Decision

- Program Name

**NT-013: Acceptance Email**

**Trigger**

Applicant Accepted

**Timing**

When student is accepted.

**Subject**

WELCOME TO 5TH YEAR🎉

Subject: WELCOME TO 5<sup>TH</sup> YEAR🎉 

 

Hi \[First Name\], 

Congratulations! You’ve been accepted into the 5th Year program for Fall 2027! 🎉This is just the beginning! 

Your Next Step:  

👉 CLICK HERE to accept or decline your spot in the 5<sup>th</sup> Year 2027-2028 Cohort 

We’re so excited about what’s ahead for you! As a 5th Year Trailblazer, you’ll discover countless opportunities to grow, learn, and explore. Once your spot is confirmed, we will begin sharing next steps with you over the coming weeks and months to help you prepare for the journey ahead! 

We look forward to working with you! If you have any questions, contact us at 419-865-5511or my5thyear@ja.org. 

Congratulations, again! 

**Dynamic Fields**

- First Name

- Cohort Year

- Accept/Decline Link

**NT-014: Applicant Declines Offer**

**Trigger**

Applicant does not accept offer.

**Timing**

When student does not accept.

Subject: Wishing You the Best, \[First Name\]! 

 

Hi \[First Name\], 

Thank you for letting us know about your decision regarding your 5th Year offer. 

While we’re sorry that you won’t be joining us, we’re grateful that you considered 5th Year and took the time to go through the application process. 

We wish you the very best in your future steps. 

Good luck — we’re cheering you on! 

**Dynamic Fields**

- First Name

- Program Name

- Decision Status

**NT-015: Accepted Applicant Next Steps**

**Trigger**

Applicant accepts offer.

**Timing**

When student accepts.

Subject:

Hi **\[First Name\]**,

Congratulations! 🎉

We are excited to confirm that you have successfully accepted your offer for the **5th Year Program for Fall \[Program Year\]**. Welcome to the **5<sup>th</sup> Year Program**!

Your journey as a **5th Year** officially begins now. We are thrilled to have you join this experience and look forward to supporting you as you continue to grow, learn, and explore new opportunities.

**Your Next Steps:**

👉 **\[CLICK HERE\]** to access your 5th Year program portal and complete your upcoming requirements.

Once your acceptance is confirmed, we will share additional details regarding onboarding activities, important dates, program preparation, and other next steps over the coming weeks and months.

We are excited to have you with us and cannot wait to see all that you accomplish!

If you have any questions, please contact us at **\[Contact Number\]** or **\[Support Email Address\]**.

Congratulations again, and welcome to the **5th Year Program! 🎉**

**Best Regards,**  
**\[Organization Name\] Team**

**Dynamic Fields**

- First Name

- Cohort Information

- Next Steps Content

- Contact Information

**5. Notification Management Business Rules**

**NT-BR-001**

System shall trigger notifications based on applicant lifecycle state changes.

**NT-BR-002**

System shall prevent duplicate email notifications for the same lifecycle event.

**NT-BR-003**

Every email shall maintain applicant reference, trigger event, timestamp, and delivery status.

**NT-BR-004**

Reminder emails shall only trigger when the required applicant action is incomplete.

**NT-BR-005**

Rejected applicants shall not receive progression emails after rejection status.

**NT-BR-006**

Accepted applicants shall receive next-step communication only after acceptance confirmation.

**NT-BR-007**

All email templates shall support configurable static and dynamic content.
