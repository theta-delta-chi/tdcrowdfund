# TDCrowdfund
This is a crowdfunding platform meant (at least initially) for use by one group of people, the Theta Deuteron charge of Theta Delta Chi.  The final product will be a website that lets alumni donate via a crowdfunding model back to the undergraduates.  Alums need to be able to browse different projects, learn more about each one, and then make a donation.  Undergraduates need to be able to post projects with text, photos, and (potentially) video.  After a project is funded, its page should be updated with progress reports and photos and allows alumni to ask questions and find out more about how completion is going.

## Specifications

### Front-End
The application breaks down into four core "views" or user interfaces.
1. Creating projects
2. Viewing multiple projects
3. Viewing the details of one project
4. Donating to a project

#### Project Creation
The project page needs to be a compelling argument for donation, so it needs to have a multimedia presentation of what the project is.  Therefore, the project creation utility should allow for uploading text, photos, and video in its most basic implementation.  Rewards also incentivize donors, so there needs to be a way to describe donation thresholds which will be rewarded (i.e. Donate $1000 to a party and we'll run around with a GoPro making people say, "Thank you, *alum name here*!").  Broadly, projects will fall into certain categories like parties, renovations, or philanthropy, so each project should have its category specified.

Some projects only work if a certain threshold is met (i.e. We can't buy half a fridge), whereas others can work with less money but have to be scaled down (i.e. "Fine, it'll be a 100 person party instead of 500.").  To accomodate this, triggered or automatic donation is a setting which is used on a project-to-project basis.  Lastly, the project must also specify a final deadline after which no more funds may be collected.

#### Browsing Multiple Projects
Since this platform isn't meant for hundreds of projects trying to advertise to millions of people, the goal when browsing is not to maximize the number of projects a user can see.  Instead, the goal is to give each project enough space to show off why it is worth donating to.  This entails a high resolution image, a few sentences of text, and the project's meta-information (category, triggered vs. automatic, current funding, deadline).  To give each project some breathing room, there should be no more than five displayed on any given browse page.

Specifics of the user interface aren't yet set in stone, but two potential libraries to use would be [FullPage.js](https://github.com/alvarotrigo/fullPage.js#fullpagejs) or [skrollr](https://github.com/Prinzhorn/skrollr).  They handle full-page scrolling and parallax scrolling, respectively.

#### Viewing Details on One Project
When examining one project, it needs to fully sell itself.  This means a lenghtier explanation (>750 words), more images in a slideshow, and potentially a video.  Additionally, the project view page needs to display all the donation rewards and the basic meta-information.  This should essentially rip off Kickstarter's UI.  Put the project video, images, and text on the left -- the meta-information and project rewards on the right.  The meta-information should communicate current funding, funding goal, remaining time, category, and funding mechanism in one glance-able box.

Ideally, the current funding 

#### Donating to a Project

### Back-End