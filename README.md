# How long has this been going on?

Since coronavirus-related disruptions have interrupted all aspects of every day life, it’s been hard to keep track of time. 
This app counts the days that have elapsed from certain events to today. It uses the svelte framework and the [World Time API](https://worldtimeapi.org/) 
to get the current time (as this is a Minnesota-focused project, all times are for the Central U.S. time zone).

## Installing
Install the dependencies...

```bash
cd minnpost-how-long
npm install
```

## Run locally for development

```bash
npm run dev
```

Navigate to [localhost:5000](http://localhost:5000).

## Build
```bash
npm run build
```

Then copy the files in the `/public/build/` folders to the relevant S3 or directory or other hosting solution.
