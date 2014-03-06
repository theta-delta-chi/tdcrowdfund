# TDCrowdfund
This is a crowdfunding platform meant (at least initially) for use by one group of people, the Theta Deuteron charge of Theta Delta Chi.  The final product will be a website that lets alumni donate via a crowdfunding model back to the undergraduates.  Alums need to be able to browse different projects, learn more about each one, and then make a donation.  Undergraduates need to be able to post projects with text, photos, and (potentially) video.  After a project is funded, its page should be updated with progress reports and photos and allows alumni to ask questions and find out more about how completion is going.

## Specifications

### Front-End
The application breaks down into three core "views" or user interfaces.

1. Creating projects
2. Viewing multiple projects
3. Viewing the details of one project

#### Project Creation
The project page needs to be a compelling argument for donation, so it needs to have a multimedia presentation of what the project is.  Therefore, the project creation utility should allow for uploading text, photos, and video in its most basic implementation.  Rewards also incentivize donors, so there needs to be a way to describe donation thresholds which will be rewarded (i.e. Donate $1000 to a party and we'll run around with a GoPro making people say, "Thank you, *alum name here*!").  Broadly, projects will fall into certain categories like parties, renovations, or philanthropy, so each project should have its category specified.

Some projects only work if a certain threshold is met (i.e. We can't buy half a fridge), whereas others can work with less money but have to be scaled down (i.e. "Fine, it'll be a 100 person party instead of 500.").  To accomodate this, triggered or automatic donation is a setting which is used on a project-to-project basis.  Lastly, the project must also specify a final deadline after which no more funds may be collected.

#### Browsing Multiple Projects
Since this platform isn't meant for hundreds of projects trying to advertise to millions of people, the goal when browsing is not to maximize the number of projects a user can see.  Instead, the goal is to give each project enough space to show off why it is worth donating to.  This entails a high resolution image, a few sentences of text, and the project's meta-information (category, triggered vs. automatic, current funding, deadline).  To give each project some breathing room, there should be no more than five displayed on any given browse page.

Specifics of the user interface aren't yet set in stone, but two potential libraries to use would be [FullPage.js](https://github.com/alvarotrigo/fullPage.js#fullpagejs) or [skrollr](https://github.com/Prinzhorn/skrollr).  They handle full-page scrolling and parallax scrolling, respectively.

#### Viewing Details on One Project
##### Before It's Funded
When examining one project, it needs to fully sell itself.  This means a lenghtier explanation (>750 words), more images in a slideshow, and potentially a video.  Additionally, the project view page needs to display all the donation rewards and the basic meta-information.  This should essentially rip off Kickstarter's UI.  Put the project video, images, and text on the left -- the meta-information and project rewards on the right.  The meta-information should communicate current funding, funding goal, remaining time, category, and funding mechanism in one glance-able box.

This is also the page where alumni hit the actual donate button.  It needs to be prominent and immediately eye-grabbing.  We should have nothing to do with the actual donation and payment process.  Assuming we integrate PayPal's Crowdfunding mechanism, PayPal should handle all transfer of funds from alums to the fraternity's account.  Credit cards should never be stored in our site, for security reasons.  Additionally, alums should be able to compare their donation to those made by their peers.  This could be done easily with a leaderboard, or there could be a more involved method like a space-filling visualization.  Letting alumni compete to donate more will only benefit us, so we should make it as easy as possible.

##### After It's Funded
Nobody wants to donate to something and never hear about it again.  Once a project is funded, it's funding page becomes an update page for alumni to check in and see how it is doing.  Alums should be able to see the same type of content they had on the pitch, so it needs room for photos, videos, and text.  However, these updates will likely be incremental and produce more media.  Therefore, the UI should break apart the content from each round of updates, with the original pitch included at the bottom (with a link to jump to it at the top of the page).  Each update box should allow for insertion of text, photo, and video.  Additionally, alumni who donated to a project should be automatically notified when it is updated.

### Back-End
The back-end of this webapp will most likely be written in Flask, since it's what I know going into this.  I would also like to incorporate [node.js](http://nodejs.org/) to give the app some more realtime features, but learning new technologies is not the primary goal on this project.  The underlying requirements of our desired functionality are:
- Storing all of the content related to each project, including: text, photos, videos, rewards, meta-information, funding status, and updates.
- Send users to PayPal's site to process their payments, and then get a confirmation of the amount donated
- Creating new projects with the aforementioned attributes.

#### Database Design

#### PayPal Functionality
Our payment processing will be entirely handled by PayPal, since it has a built-in crowdfunding account and absolves us from security concerns.  More specifically, we will be using the [Adaptive Payments API](https://developer.paypal.com/docs/classic/products/adaptive-payments/) to handle the specifics of accepting payment.  Ideally, our integration is as simple as a button to send users to PayPal and a receipt once the donation has gone through.