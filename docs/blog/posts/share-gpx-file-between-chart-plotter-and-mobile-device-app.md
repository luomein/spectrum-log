---
date: 2025-01-19
authors:
  - luomein
categories:
  - app
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

You could manually save the active track for future reference, but some of the realtime information will be lost. If you save the active track and export it, some GPX viewer, for example, iOS Garmin Navionics Boating app will not read it correctly due to the realtime information lost.

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

    In saved track,
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
