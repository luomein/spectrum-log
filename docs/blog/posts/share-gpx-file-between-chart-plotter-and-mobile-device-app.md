---
date: 2025-01-19
authors:
  - luomein
categories:
  - app
  - Garmin GPSMAP 722xs Chart Plotter
description: >
  Notes on using GPX file for export/import chart routes, tracks and waypoints when it works and when it not.
title: Share GPX file between chart plotter and mobile device app
---

# Share GPX file between chart plotter and mobile device app

__GPX, or GPS exchange format, is an XML file format for storing coordinate data. It can store waypoints, tracks, and routes. However different GPX viewer handle tracks differently so that sharing tracks sometimes fail. You need to know some implicit rules in order to share tracks successfully. On the other hand, sharing routes and waypoints are more straitforward.__

Working envoronment: Garmin GPSMAP 722xs Chart Plotter, iOS Garmin Navionics Boating app, microSD card reader.

Limited condition: Garmin GPSMAP 722xs Chart Plotter is registered under previous owner so that ActiveCaption app can not be used for direct export/import.

Best Practice: Export the tracks in the Active Track in the Garmin GPSMAP 722xs Chart Plotter before saving the tracks to files.

<!-- more -->

## Active Track

In Garmin GPSMAP 722xs Chart Plotter, the track currently being auto recorded is called the active track. It is stored in the track memory. If the memory is full, it may stop recording or overwriteing depending on the user setting.

You could manually save the active track for future reference, but some of the realtime information will be lost. 

!!! example "Compare tracks information"
    In active track,
    ```gpx
            <trkpt lat="22.4375212938" lon="120.4761361610">
                <time>2024-12-05T08:40:47Z</time>
                <extensions>
                    <gpxtpx:TrackPointExtension>
                        <gpxtpx:wtemp>24.26</gpxtpx:wtemp>
                        <gpxtpx:depth>3.46</gpxtpx:depth>
                    </gpxtpx:TrackPointExtension>
                </extensions>
            </trkpt>
    ```

    In saved track, the timestamp information is lost.
    ```
            <trkpt lat="21.9477193337" lon="120.7459062897">
                <extensions>
                    <gpxtpx:TrackPointExtension>
                        <gpxtpx:wtemp>21.98</gpxtpx:wtemp>
                        <gpxtpx:depth>3.24</gpxtpx:depth>
                    </gpxtpx:TrackPointExtension>
                </extensions>
            </trkpt>
    ```

## GPX Viewer

How to handle GPX file is dependent on the GPX viewer itself. 

### iOS Garmin Navionics Boating app

It requires tracks to have timestamp information.

Active track can be shown in the iOS Garmin Navionics Boating app because it has timestamp information.

If you save the active track and export it, the iOS Garmin Navionics Boating app will not read it correctly due to the timestamp information lost.

For the same reason, if you convert a route to track, the iOS Garmin Navionics Boating app will not read it correctly due to the lack of timestamp information.

On the other hand, there is no special requirements on routes and waypoints. If you convert a track to a route then the iOS Garmin Navionics Boating app can show it. But the problem is, it will look odd because route is assumed for passage planning with sparsed points. The track-converted route has too much points to show.

  [track-converted route]: share-gpx-file-between-chart-plotter-and-mobile-device-app/track-converted-route.png

  [test]: the-past-present-and-future/mkdocs-material-0.1.0.png

### Garmin BaseCamp app

All tracks including active track and saved tracks can be shown on the Garmin BaseCamp. No special requirements.

### Relive app

It requires tracks to have timestamp information.

It uses the term 'route' to refer to the track in the GPX file. It can not read routes and waypoints info in the GPX file.

On iOS Relive app, it can not access the gpx file in the iOS file system. Maybe it is a bug. I use a Mac and the Relive website to import GPX file.

## Summarize
  
| GPX Content      | iOS Garmin Navionics Boating app  |  Garmin BaseCamp app      |  Relive app |
| ----------- | ------------------------------------ | --------------------- | -- |
| active track       | :material-check:     |:material-check:     |:material-check:     |
| saved track       | :material-close:   |:material-check:     | :material-close:  |
| route-converted track    | :material-close:     |:material-check:     |:material-close:   |
| route  | :material-check:     |:material-check:     |:material-close:   |
| track-converted route  | :material-check:     |:material-check:     |:material-close:   |
| waypoints  | :material-check:     |:material-check:     |:material-close:   |






