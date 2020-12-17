# GOUPIL WORKLOAD OVERVIEW

## Visual & content
### Overall design
- Typography
- Colors
- Page layout (mobile / tablet / laptop)
### Individual pages
- Home page
- Default content pages (e.g. "Association", "Education" etc.)
- HFS page
- Contact page
- Events page
- Sponsors / partners page
- Tutorials page (adherants only)
- Shop pages: storefront, category views, detail views
- Newsletter default email templates
- Header / Footer
### Content creation
- Clarify main-menu structure
- Home page texts & visuals
- Initial texts for each page
- Graphic design (icons etc.)
- Photos selection
- Scrape existing content from the current site that needs to be preserved or archived
    - Identify which part(s) of the site are to be kept
    - Write the spiders (web-crawl scripts)
    - Export texts / visuals in consistent data structures
## Development
### HTML / CSS / templates
- The designs above need to be "reproduced" on the browser (for all screen sizes)
- Navigation menu(s)
### User management (mostly out-of-the-box, slight customizations):
- User management system 
- User roles / permissions i.e. admins, authors, volunteers (mostly out-of-the-box, slight customizations)
- GDPR compliance ( users must be able to view / download / delete any of their own data  we keep )
### CMS customization (mostly out-of-the-box, slight customizations):
- Custom toolbar buttons and plugins for (even) easier content creation
- Unit tests
### Blog application (mostly out-of-the-box, slight customizations)
- Configuration
- Templates customization / styles to match design
### Email back-end (for emails sent programmatically)
- Integration with an email delivery app (e.g. mailgun, sendinblue, sendgrid etc.) This ensures emails are not blocked nor end up in the spam folder.
- Unit tests
### SEO optimization
- Template work
- django-page-meta configuration
### Cookie-consent-management
- Cookiebot integration (https://www.cookiebot.com/fr/)
### Shop application
- Snipcart intagration (https://snipcart.com/) 
- Product / product categories models and templates
- Payment gateway
- Unit tests
Disclaimer: snipcart will charge 1.5% of your sales if your sales are over 500€/month
### Donation/adherants application
- Integration with helloasso API ( https://dev.helloasso.com/v3/responses#paiements )
- Unit tests
### Intranet
- Adaptation to any custom User roles/permissions
- File organisation utils (custom upload locations, folder creation etc.)
- Potential external storage integration (e.g. S3)
- Unit tests
### Social-media management
- page-meta attributes
- Auto-publish blog posts on fb, instagram via their graph-APIs
- Unit tests
### Video tutorials
- Restricted pages url config (for adherants only - else redirect to "become adherant page")
- Choose video-hosting platform (e.g. YouTube, DailyMotion, Vimeo) and create Goupil account
- Easy embedd via CMS plugin
- Unit tests
### Newsletter
- Maintain subscribers' mailing list(s)
- 2-way synch with external API for mail-delivery / marketing service
- Asynchronous task (span big campaigns over several days not to exceed 300 emails per day limit)
- Unit tests
### Events
- Event model
- Enable filtering (by event_type or by users permissions)
- Interactive map integration ( https://leafletjs.com/ )
- Calendar
- Intranet integration (recurrent events / scheduling)
- Unit tests
### Counter plugin
Show a counter of hours-of-work / number-of-animals for any given day
- model, view, tempates
- Unit tests

## Migration & infrastructure
- Switch to cloud infrastructure (within OVH or other)
- DNS changes ("transfer" domain name to new site)
- email solution (for setting up @goupilconnection.org mailboxes)
    - setup required accounts
    - migrate existing email archives
- schedule database backups

## Collaboration
### Additional meetings
- Precise design specs
- Validate content
- Precise extra functionalities
- Feedback iterations
### Training
- CMS usage for admins
- CMS usage for volunteers
- Blog post creation
- Social media management
- Search Engine Optimization
- Newsletter / Campaigns
- Web shop (catalogue / order processing)
## Support
- Software updates
- Inrastructure monitoring

## Technical details
For the tech savvy here is a list of the proposed stack:
**Docker** is used for containerizing the application (https://www.docker.com/)
### Services
- Back-end:
    - language: python (https://www.python.org/)
    - framework: django (https://www.djangoproject.com/)
    - Content Management System: djangoCMS (https://www.django-cms.org/en/)
- Database: Postgresql (https://www.postgresql.org/)
- Caching / message broker: Redis (https://redis.io/)
- Task queue / scheduler: Celery (https://docs.celeryproject.org/en/stable/)
- Search engine: elastisearch (https://www.elastic.co/elastic-stack)
### Devops
- Version control: git (https://git-scm.com/)
- Duplicated staging and live server environments
- Automated pipelines for testing & continuous deployment
- Automated software updates via dependabot (https://dependabot.com/)
- log monitoring via sentry (https://sentry.io)
## Estimated annual operational costs
- Cloud hosting: ~6€ / month => ~75€ / year
- Domain name costs: ~ 10 / year
- Cookiebot: free for < 500 pages
- email hosting : depends on number of mailboxes: ~ 15€ / year
- email delivery / marketing service: free for 300 emails/day (this is for emails sent FROM the web application)
**Overall : ~ 100€ year**
