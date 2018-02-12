
Andrew Steinmetz

SER 402 Spring 2018

Professor Acuna

# Individual Contribution Report

Since our last team review meeting, below are the links to my pull requests that got merged into our repository. All code written in these pull requests are my own. 

## Merged Pull Requests

Refactor survey landing page fragment into MVP which turned into a bigger refactor of our mainactivity as well into MVP to get everything working.

[https://github.com/arsteinm/safety-app/pull/16](https://github.com/arsteinm/safety-app/pull/16)

Refactor location fragment into an activity following the MVP pattern. 

[https://github.com/arsteinm/safety-app/pull/18](https://github.com/arsteinm/safety-app/pull/18)

Refactored summary landing page into MVP pattern. 

[https://github.com/arsteinm/safety-app/pull/15](https://github.com/arsteinm/safety-app/pull/15)

Added a tutorial page to show user how to create a survey which will only show after first launch. 

[https://github.com/arsteinm/safety-app/pull/13](https://github.com/arsteinm/safety-app/pull/13)

## Commit Log

```
commit f0efec4b6f4974d8c3b9cc400ce91d5d049e375b (HEAD -> arsteinm/US-23, origin/arsteinm/US-23)
Merge: 3956473 e09cce3
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Thu Feb 8 18:44:24 2018 -0800

    Merge branch 'master' into arsteinm/US-23

commit e09cce3a7eb42e9dd562bd40aa29be9b8495666c
Merge: d485498 48f5bfd
Author: Robert Beerman <rbeerma@asu.edu>
Date:   Thu Feb 8 17:48:40 2018 -0700

    Merge pull request #21 from arsteinm/rbeerma/hotfix-crashOnCreateNewSurvey

commit f0efec4b6f4974d8c3b9cc400ce91d5d049e375b (HEAD -> arsteinm/US-23, origin/arsteinm/US-23)
Merge: 3956473 e09cce3
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Thu Feb 8 18:44:24 2018 -0800

    Merge branch 'master' into arsteinm/US-23

commit e09cce3a7eb42e9dd562bd40aa29be9b8495666c
Merge: d485498 48f5bfd
Author: Robert Beerman <rbeerma@asu.edu>
Date:   Thu Feb 8 17:48:40 2018 -0700

    Merge pull request #21 from arsteinm/rbeerma/hotfix-crashOnCreateNewSurvey

    Rob/Hotfix for crash when clicking create new walkthrough button
    
    commit ea3a0cf6f0f0f561bbfc660ed2b78fcc9e574dd8 (HEAD -> arsteinm/US-22, origin/arsteinm/US-22)
Merge: a915435 806a548
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Fri Feb 2 00:27:33 2018 -0800

    Merge branch 'master' into arsteinm/US-22

commit a915435a9686321b6b62d14dc069612488b2f81f
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Fri Feb 2 00:24:37 2018 -0800

    fix title change when page changes

commit 5289106adc5a2c6774d61172349054ebd074dacf
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Fri Feb 2 00:05:31 2018 -0800

    fab will dissappear and reappear

commit cb5898f5ce5d0d4640515d5fa70a5232423a55d7
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Thu Feb 1 23:51:46 2018 -0800

    refactored main activity into mvp

commit 0dacf0f9bc8777e7d8dc0b990cf6b243e2cc7b93
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Thu Feb 1 23:18:48 2018 -0800

    refactored summary, action items, and survey landing to instantiate presenter from main activity

commit 482e334226d69b4f557a38d3b20eb2ffd995b7b1
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Thu Feb 1 22:03:32 2018 -0800

    add base presenter and view

commit ad0aa39be2daf63c7782d9881a10aabe82784fe3 (HEAD -> arsteinm/mvp-summary, origin/arsteinm/mvp-summary)
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Thu Jan 25 00:25:38 2018 -0800

    refactored summary landing page into mvp. Might need to refactor SurveyOverview to have a summary model?

commit e72eeabead134df0231e9778d427430677340119
Merge: 4fa3e53 cdecb55
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Tue Jan 23 20:34:34 2018 -0800

    Merge pull request #13 from arsteinm/arsteinm/US-03

    Arsteinm/us-03 Tutorial to click on add survey button

commit cdecb55fb303e495660a810a7ebcfb1529c05fde (origin/arsteinm/US-03)
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Tue Jan 23 01:24:31 2018 -0800

    moved the location of the tutorial removal button and disable fab and made invisible view appear to block clicking on recyclerview behind the overlay

commit c843a29ad1c97f8bbd85b67ec286fc37e8201734
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Sun Jan 21 01:40:20 2018 -0800

    showcase view will disappear if touched anywhere on the screen

commit dba7573907f7a70798bda08071532a9e01303889
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Sun Jan 21 01:35:54 2018 -0800

    showcase view will only launch on first startup

commit dcc51dad8b2a4d9dffc6562e686af9dfa83206d7
Author: Andrew Steinmetz <arsteinm@asu.edu>
Date:   Thu Jan 18 01:44:06 2018 -0800

    added showcaseview to highlight the add button to create a survey.
    Still need to implement logic for only launching at first launch
    
    
```

