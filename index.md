---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "UKAEA"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "Culham Science Centre, E6, Training Room"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "GB"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "English"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: 51.65713      # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: -1.23002     # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "2, 3, 9, 10, 18, 19 June 2025"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "13:00 - 16:30 GMT (UTC+0)"    # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2025-06-02      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2025-06-19
instructor: ["Matthew Bluteau", "Kirill Palamartchouk", "Kristian Zarebski", "Matthew Field", "Harry Saunders", "Kingsley Collie"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Sanket Gadgil"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["matthew.bluteau@ukaea.uk"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes: "https://codimd.carpentries.org/ukaea-int-rsd-20250602#" # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}

{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% if site.pilot %}
This is a pilot workshop, testing out a lesson that is still under development. The lesson authors would appreciate any feedback you can give them about the lesson content and suggestions for how it could be further improved.
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://www.latlong.net/ to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  Calendar invites will be sent to all participants.
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have a user
    account on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.).
  {% endif %}
  They should have a few specific software packages installed (listed <a href="#setup">below</a>).
  UKAEA-managed Windows machines have restricted permissions but should be able
  to install the requisite software. Please see instructions below for further
  details.
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
{% if online == "false" %}
  We are committed to making this workshop accessible to everybody. If we can
  help making learning easier for you (e.g. sign-language interpreters,
  lactation facilities) please get in touch (using contact details below) and we
  will attempt to provide them.
</p>
{% else %}
  We are dedicated to providing a positive and accessible learning environment for all. Please
  notify the instructors in advance of the workshop if you require any accommodations or if there is
  anything we can do to make this workshop more accessible to you.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>

{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in this
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to software as described below.
  In addition, you will need an up-to-date web browser.
</p>

{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% elsif site.carpentry == "incubator" %}
All non-Windows users, please check the note below about IDEs,
then head to the "Setup" page of [the lesson site]({{ site.incubator_lesson_site }}installation-instructions)
for instructions to follow to obtain the software and data you will need to follow the lesson.
For Windows users, please see the note immediately below.
We recommend that you use your work laptop for the course and run the software required directly on that.

We appreciate that some participants will work on Linux clusters on a regular basis
(e.g. freia, heimdall, cumulus) and will therefore want to do the course work from there.
Whilst this is possible,
the Python installation on these clusters is not in a suitable state for the course.
We have frequently run into problems trying to complete the course content in these environments.
**Therefore, we strongly discourage you from using one of these clusters at this time.**
If you still wilfully choose to work on a cluster, please be aware our support for you will be
limited.[^1]

[^1]: There is ongoing work to improve the Python installation on UKAEA clusters,
      so we hope it will soon be possible to offer this as a viable option again.

>## Some notes for UKAEA Windows users
>
> It has been our experience that installing GitBash as recommended in the
> course setup is not a workable option. Instead, learners have had much less
> trouble if they use WSL (Windows Subsytem for Linux) and connect the VS Code
> IDE to that. We therefore recommend the following setup steps:
>
> 1. Follow [the instructions to install
>    WSL2](https://intranet.ukaea.uk/software/guides/wsl2.html) on your UKAEA
>    laptop if you don't already have it. You do not need to use one of the pre-built distributions.
>    Just use the Ubuntu distribution from the Windows Store.
> 2. Follow [the link at the bottom of that
>    guide](https://code.visualstudio.com/docs/remote/wsl) to get VS Code
>    connected to WSL2. Within WSL2, we recommend you work within the default
>    home directory that the terminal places you in. **Do not work from a
>    directory in your roaming profile, shared home directory, or OneDrive
>    synchronised directory.**
> 3. Alternatively, if you prefer PyCharm as your IDE, then you can install it
>    within WSL and launch it from there (update the PyCharm version data as neeed):
>
>    ```bash
>    wget https://download.jetbrains.com/python/pycharm-community-2024.1.1.tar.gz
>    sudo tar xzf pycharm-*.tar.gz -C /opt/
>    alias pycharm=/opt/pycharm-community-2024.1.1/bin/pycharm.sh  # Put this into .bashrc
>    pycharm
>    ```
>
>    By default, WSL2 should automatically be able to launch graphical
>    applications, but this is new functionality and not yet reliable, so please
>    reach out for help if you encounter problems. Make sure you have [set the
>    default WSL
>    version](https://learn.microsoft.com/en-us/windows/wsl/basic-commands#set-default-wsl-version)
>    to `2`.
>
> 4. If you have any problems along the way, contact one of the course helpers,
>    or raise it at the first session.
>
> If the above fails, you can fall back to the option of using GitBash and a
> local Python installation:
>
> - Git for Windows can be installed using the Software Center/Application Catalog.
> - You can download and run a standard Python installer from
>   <https://www.python.org/downloads/windows/>, but should ensure that the
>   option to install for all users is not selected (to avoid the need for admin
>   privileges).
> - Get your IDE. We recommend VS Code which can be installed from the Windows
>   Store. The PyCharm installer can be run using your standard login (and
>   without an admin account).  It is important to choose an installation path
>   where you have write permissions (i.e. not the default path). The PyCharm
>   installer probably won't run perfectly without admin rights, but our testing
>   has shown that it does yield a functional application. In particular, you
>   might notice it fails to create a shortcut from the start menu.
{: .callout}

>## A note about IDEs
>
> There are two Integrated Development Environments (IDEs) that are supported
> for this course, and we recommend that you use one of them:
>
> 1. JetBrains' PyCharm: this is the one recommended in the course setup pages,
>    and it is the IDE used throughout the examples in the course content. All
>    figures and instructions relate to it.
> 2. Microsoft's VSCode: a widely used IDE and likely the most popular at UKAEA.
>    Instructions for getting set up with it have recently been added to the
>    ["Extras" of the
>    course](https://carpentries-incubator.github.io/python-intermediate-development/vscode/index.html).
>    As you go through the course and features of PyCharm are being explained,
>    you can use that document to get the analogous features in VSCode. This
>    will of course require switching between between webpages, so the
>    experience will not be as seamless. A better UX is in our long term plans.
>
> However, because this is an intermediate-level course,
> we expect that a number of participants will already have some experience using an IDE or comparable advanced code editor
> (e.g. Vim, Emacs).
> Therefore, you are welcome to use your editor of choice for the course
> if you are confident that you can achieve similar functionality that is described for PyCharm:
>
> - Syntax highlighting, indentation, and autocompletion
> - Recognition of virtual environments and setting the correct Python interpreter
> - Running the Python debugger from the IDE and setting breakpoints at specific lines
> - Integration with pytest and the ability to launch individual tests from the
>   editor
>
> Also, you must accept the provision that we will only support the two IDEs above.
> Regardless of your decision, we recommend that you still install one of the editors above as a fallback.
{: .callout}

{% endif %}

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}
{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

<hr/>

{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>There will then be a post-course survey to collect your feedback
about how the sessions went.</p>
{% if site.carpentry == "incubator" %}
<p><a href="{{ site.incubator_post_survey }}">Post-course Survey</a></p>
{% elsif site.incubator_pre_survey or site.incubator_post_survey %}
<div class="alert alert-danger">
WARNING: you have defined custom pre- and/or post-survey links for
a workshop not configured for The Carpentries Incubator
(the value of `curriculum` is not set to `incubator` in `_config.yml`).
Please comment out the `incubator_pre_survey` and `incubator_post_survey` fields
in `_config.yml` or, if this workshop is teaching a lesson in the Incubator,
change the value of `carpentry` to `incubator`.
</div>
{% else %}
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">Schedule</h2>

{% include custom-schedule.html %}

This workshop is teaching a lesson in [The Carpentries Incubator](https://carpentries-incubator.org/).
Please check [the lesson homepage]({{ site.incubator_lesson_site }}) for a more detailed list of lesson sections and estimated timings.

{% comment %}
Edit/replace the text above if you want to include a schedule table.
See the contents of the _includes/custom-schedule.html file for an example of
how one of these schedule tables is constructed.
{% endcomment %}

{% if site.pilot %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. Please [contact the workshop organisers](#contact) if you would like more information about the planned schedule.
{% endif %}

<hr/>
