# tracetimer.com

The site for TRACE. Static HTML, no build step, no framework: three pages
and a folder of icons. Hosted on GitHub Pages under the custom domain.

    index.html           the landing page
    privacy/index.html   the privacy policy (the URL the stores ask for)
    support/index.html   FAQ and the support address
    img/                 icon at web sizes, from the app's own master
    media/               (create it) the reel clip and its poster frame
    CNAME                tracetimer.com — GitHub Pages reads this

## Deploy

1. GitHub → New repository → `tracetimer.com`, **public** (Pages on a
   private repo needs a paid plan), no README. Then from this folder:

       git remote add origin https://github.com/Stonewallkid/tracetimer.com.git
       git push -u origin main

2. Repository → Settings → Pages → Source: "Deploy from a branch", branch
   `main`, folder `/ (root)`. Custom domain: `tracetimer.com`. Tick
   **Enforce HTTPS** once the certificate shows (minutes to an hour).

3. At the registrar's DNS for tracetimer.com:

       A      @     185.199.108.153
       A      @     185.199.109.153
       A      @     185.199.110.153
       A      @     185.199.111.153
       CNAME  www   stonewallkid.github.io

   Same records lazymanlabs.com uses. DNS takes minutes to a day.

Every later change: edit, commit, `git push`. Live in about a minute.

## Dropping in the clip

Export the reel from the app, save it to the phone, get it onto the Mac,
then `media/reel.mp4` plus a poster frame `media/reel.jpg`. In
`index.html`, replace the "A clip goes here" line with the `<video>` tag
in the comment beside it. Keep the file under ~20 MB; GitHub serves it
straight from the repository.

## Beta builds

The Android APK is a GitHub Release on this repo, always uploaded under
the asset name `trace-beta.apk`, so the site's download button
(`releases/latest/download/trace-beta.apk`) never changes. In the app repo,
`tool/beta_build.sh <date>` cuts a build and `tool/beta_publish.sh` uploads
it here. When TestFlight and Play links exist, the comment in the `#beta`
section of `index.html` shows the buttons to add.
