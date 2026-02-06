# SEPTA Bus and Metro - GTFS Feed 
## Changelog

### v202602150

Bus/Metro
* The weeklong trolley (T routes) tunnel closure previously scheduled from 10 pm on February 13 through 5 am February 23 has been shortened to a weekend only closure from 10 pm on February 13 until 5 am February 16. The "T Bus" remains in service on weekends only. See [septa.org/news/trolley-tunnel-update/](https://wwww.septa.org/news/trolley-tunnel-update/) for more details.
* The Spring schedule change for most Bus and Metro routes will take effect Sunday, Feb. 22. Changes for routes M1, D1, D2, and some suburban bus routes will take effect Monday, Feb. 23. (This feed takes effect seven days earlier, on Feb. 15, and contains seven days of the Fall schedule in addition to the upcoming Spring schedule.)
* New Fares v2 information: New files and fields define standard single-journey fare information. Additional media, products, rules, and categories may be added in the future. See [here](https://wwww.septa.org/fares/) for more fare information.
  * New files: files fare_leg_rules.txt, fare_media.txt, fare_products.txt, fare_transfer_rules.txt, and rider_categories.txt 
  * New fields: `routes.network_id`, `agency.agency_fare_url`, `agency.cemv_support`
* New routes "D1 Bus" and "D2 Bus" (`route_id` values in uppercase: "D1 BUS" and "D2 BUS") are weekend bus replacement services for routes D1 and D2. See [here](https://wwww.septa.org/news/d1-d2-shuttle-busing/) for more details.
  * T Bus, T5 Bus, and FOX Bus routes remain in service.
* T routes, G1, and formerly lettered bus routes have had their `routes.route_long_names` updated to remove references to their former names. (E.g. T1's long name is now "13th St to 63rd-Malvern/Overbrook" instead of "Route 10"). Also, routes.txt has been reordered into a more natural ordering. The `routes.route_sort_order` field may be provided in the future.
* Loop routes 35, 310, LUCYGO, and LUCYGR have their first stop marked as pickup only and last stop marked as drop off only to address confusing next-to-arrive information.
* New `trips.bikes_allowed` information for all bus and Metro trips. See [here](https://wwww.septa.org/bikes/) for more guidelines.
* New `trips.wheelchair_accessible` information for all bus and Metro trips, and updated `stops.wheelchair_boarding` information for Metro stations where appropriate. 
* Several `service_id` values and associated trips are not scheduled to be active on any date, but intentionally remain in the GTFS-Schedule data. These are alternate services/patterns/trips that may be used as `TripUpdate.schedule_relationship=DUPLICATED` trips in GTFS-realtime data if needed in case of schedule changes on short-notice.
* Other minor stop and schedule changes.

Regional Rail
* New fields provide basic fare information: `agency.agency_fare_url`, `agency.cemv_support`. Fares v2 data may be added in the future.

### v202602010

Bus/Metro
* Fixes to T line schedules. T routes resume service in the tunnel during daytime on weekdays. T routes continue to serve 40th-Market/Filbert late nights and weekends. The "T Bus" remains in service on weekends only. See [septa.org/news/trolley-tunnel-update/](https://wwww.septa.org/news/trolley-tunnel-update/) for more details.
* Other minor stop and schedule changes.

Regional Rail
* New Regional Rail schedules. See [here](https://wwww.septa.org/news/regional-rail-schedules/) for more details.
* Adds `stops.wheelchair_boarding`, `trips.wheelchair_accessible`, and `trips.bikes_allowed` information for all Regional Rail stations and trips.
* Updates Regional Rail stop names to follow systemwide naming conventions.

### v202601140

Bus/Metro
* Revised stops on Oregon Avenue in relation to new bus lane markings. See [septa.org/news/red-bus-only-lanes/](https://wwww.septa.org/news/red-bus-only-lanes/) for more details.
* Resolved an issue with duplicate block names on routes L1, B1, B2, and B3.
* T routes resume service in the tunnel during daytime on weekdays. T routes continue to serve 40th-Market/Filbert late nights and weekends. The "T Bus" remains in service on weekends only. See [septa.org/news/trolley-tunnel-update/](https://wwww.septa.org/news/trolley-tunnel-update/) for more details.
* Redesignated T5 Bus as `route_type=3` like other shuttles, and added direction information.

Regional Rail
* Corrected Fox Chase Train #817 to originate at Wayne Junction at 9:40 am instead of Fox Chase. See [septa.org/news/fox-chase-shuttle-bus/](https://wwww.septa.org/news/fox-chase-shuttle-bus/) for more details.
* Please note that all morning express trips on Regional Rail have been restored as of Monday, January 12. See [septa.org/news/morning-express-service-restored/](http://wwww.septa.org/news/morning-express-service-restored/) for more details.

### v202512146

Bus/Metro
* Added new "T Bus" route (`route_id` "T BUS"), operating 7 days a week between 40th-Market and 15th St/City Hall. See [septa.org/news/trolley-tunnel-update/](https://wwww.septa.org/news/trolley-tunnel-update/) for more info.
* Fixed T1 calendar.
* Set FXCB calendar to start Jan. 5, 2025 to align with start of work on Fox Chase line.
* Changed FXCB `route_short_name` and `route_long_name` to match other branding.
* Changed "T5 Bus" `route_id` to "T5 BUS" (all uppercase).
* Removed expired services.
* Other minor schedule corrections.
* Note: T routes continue to serve 40th-Market/Filbert.

Regional Rail
* Minor schedule corrections.

### v202512140

Bus/Metro
* New stops and shapes for routes serving the new Wissahickon Transit Center.
* New "Fox Chase Shuttle Bus" route for upcoming work.
* T routes continue to serve 40th-Market/Filbert.

Regional Rail
* Additional New Year's Eve service now included.
* Fox Chase scheudles adjusted to reflect upcoming work.

## About this documentation   

This document describes SEPTA's "Metro" nomenclature and custom fields/files. This document also contains a changelog. 

It *is not*: 

- A comprehensive guide to SEPTA's GTFS feeds or [GTFS itself](https://gtfs.org/schedule/) 
- A comprehensive guide to SEPTA's upcoming Metro nomenclature and wayfinding overhaul. More info on the changes can be found at [septa.org/metro](https://gtfs.org/schedule)
- A guarantee that SEPTA will provide data in any particular format (though we will try our best) 
- A [license agreement](https://wwww.septa.org/license-agreement/)  

## routes.txt 

The route names of SEPTA's heavy rail (subway/elevated) and light rail (trolley) routes, and certain bus routes are [changing](https://wwww.septa.org/metro/letters-colors-symbols/). In GTFS, the new nomenclature is in the `route_short_name` field, while the old nomenclature remains in the `route_long_name`. The `route_id` field matches the `route_short_name` field, as is current practice (excpet in the case of shuttle buses). Physical signage will be replaced throughout the system over the coming months/years, expected to be completed in 2026. SEPTA's app and website display both new and old nomenclature side-by-side to support riders through this transition. **As of February 15, 2026:** T routes, G1, and formerly lettered bus routes no longer include the former route name in their `route_long_name` as signage installation progresses and we continue transitioning to the new nomenclature.

| Current route_id | Current route_short_name | Former route_long_name              | - | New route_id | New route_short_name | New route_long_name                 | 
| ---------------- | ------------------------ | ----------------------------------- | - | ------------ | -------------------- | ----------------------------------- |
| 10               | 10                       | Route 10                            | - | T1           | T1                   | 13th St to 63rd-Malvern/Overbrook   |  
| 11               | 11                       | Route 11                            | - | T4           | T4                   | 13th St to Darby Transit Center     | 
| 13               | 13                       | Route 13                            | - | T3           | T3                   | 13th St to Yeadon or Darby TC       | 
| 15               | 15                       | Route 15                            | - | G1           | G1                   | 63rd-Girard to Richmond-Westmorelnd | 
| 34               | 34                       | Route 34                            | - | T2           | T2                   | 13th St to 61st-Baltimore/Angora    | 
| 36               | 36                       | Route 36                            | - | T5           | T5                   | 13th St to 80th St/Eastwick         | 
| 101              | 101                      | Route 101                           | - | D1           | D1                   | Route 101                           |
| 102              | 102                      | Route 102                           | - | D2           | D2                   | Route 102                           |
| BSL              | BSL                      | Broad Street Line                   | - | B1           | B1                   | Broad Street Line Local             |
| BSL              | BSL                      | Broad Street Line                   | - | B2           | B2                   | Broad Street Line Express           |
| BSL              | BSL                      | Broad Street Line                   | - | B3           | B3                   | Broad-Ridge Spur                    |
| MFL              | MFL                      | Market-Frankford Lin                | - | L1           | L1                   | Market-Frankford Line               |
| NHSL             | NHSL                     | Norristown High Speed Line          | - | M1           | M1                   | Norristown High Speed Line Local    |
| G                | G                        | Overbk/LankMC to ColCom/FdDstCtr    | - | 63           | 63                   | Lanknau/Overbrk to ColCom/FdCtr     |
| H                | H                        | Broad-Erie to Cheltenham-Ogontz-H   | - | 71           | 71                   | Broad-Erie to Cheltenham-Ogontz     |
| J                | J                        | Chelten-Wisshkn to Richmond-Orthodx | - | 41           | 41                   | Chelten-Wissahckn to Richmnd-Orthdx |
| K                | K                        | Ridge-Midvale to Arrott TC          | - | K            | K                    | Ridge-Midvale to Arrott Transit Ctr |
| L                | L                        | ChestnutHill/PlymouthMtgMall to OTC | - | 51           | 51                   | Plymth Mtg/Chestnt Hill to Olney TC |
| R                | R                        | Henry-Mid or WissTC to FrankfordTC  | - | 82           | 82                   | Wisshkn TC/Henry-Midvl to FrankfdTC |
| XH               | XH                       | Broad-Erie to Cheltenham-Ogontz-XH  | - | 81           | 81                   | Broad-Erie to Cheltenham-Ogntz      |

Note that in addition to the Metro routes switching to Letter-Number pairs, bus routes that formerly used letter(s) have switched to numbers only. This is so that there are no duplicates with the new Metro letters, and so that moving forward, letters always refer to Metro routes and numbers always refer to bus routes. Specifically G, H, J, L, R, and XH are changing to numbers. Bus route K will remain "K" until it is discontinued. 

Additionally, trolley replacement routes will be added over time as they are needed. These replacement routes are temporary 1:1 replacements of trolleys with buses due to roadwork or other obstacles to trolleys that buses can navigate around. Our trolley network is largely street-running in mixed traffic, so riders will not experience a major change in boarding locations, frequencies, or amenities. Once added, they will not be removed from future feeds, even if no trips are assigned to those routes. They will have a route_id consisting of the route_id of the route they are replacing, followed by a space and the letters "BUS" (for example, route_id "T5 BUS" indicates a bus-operated service replaceing part or all of the T5 route, which is ordinarily a trolley). The route_short_name will also be “T5 BUS” (for example), and the route_long_name will be the same as the service being replaced. Please note: the bus replacement service will carry the route_type of "0" (which indicates a trolley), not "3" (which would indicate a bus). This is an intentional mismatch with the actual type of the vehicle on the street, and is done so that these temporary replacement services will be categorized as "Metro" services in our own tool and third party tools. 

In contrast, Regional Rail shuttle buses may follow a different naming scheme and will be categorized as bus services. Regional Rail shuttle bus replacement routes may not have matching route_id and route_short_name values.

## directions.txt

Provides for passenger-facing names to be documented for each direction_id value on a route-by-route basis. This specificiation adds onto the [GTFS+ directions.txt extension](https://www.transitwiki.org/TransitWiki/images/e/e7/GTFS+_Additional_Files_Format_Ver_1.7.pdf) and is based on the [experimental directions.txt extension developed by the MBTA](https://github.com/mbta/gtfs-documentation/blob/master/reference/gtfs.md#directionstxt).

Field Name | GTFS spec | Status | Notes
---------- | -------- | ------ | --------
route_id | Experimental | Included | Linked to routes.txt file.
direction_id | Experimental | Included | Binary value linked to trips.txt file. Combining `route_id` and `direction_id` forms the unique primary key for this file.
direction | Experimental | Included | Human-readable text corresponding to a direction name in a given list. Current valid values are: <ul><li>Northbound</li><li>Southbound</li><li>Eastbound</li><li>Westbound</li><li>Inbound</li><li>Outbound</li><li>Loop</li></ul>
direction_destination | Experimental | Included | SEPTA extension which provides the direction name used in other rider-facing materials and communications. Often, but not always, similar to the most common `trips.trip_headsign` for the route and direction. Destinations may include:<li>A city/town/place name: `Coatesville`, `Horsham`, or `Center City`</li><li>A point of interest or transit center: `City Hall`, `Plymouth Meeting Mall`, or `Olney Tranist Center`</li><li>A street intersection, omitting suffixes like "St." and "Ave.": `2nd-Spruce` or `Richmond-Westmoreland`</li><li>A "via" designation: `7th-Spring Garden via 9th Street` or `Broad-Oregon via PNC and UPS`</li><li>A combination of any of the above, typically indicating multiple common end-of-line destinations depending on the time of day, day of week, or stopping patern: `Henry-Midvale & Wissahickon Transit Center`, `54th-City or 50th-Parkside` or `Springfield Mall & Penn State`</li>

## route_stops.txt

Provides a list of stops associated with each route in each direction, ordered in a way that is ideal for presentation to riders. While `stop_times.txt` describes the sequence of stops for a particular trip, not all trips of a given route make the same stops. This file provides a list of _all_ stops served by a particular route in a particular direction, without duplicate stops. This is helpful for "pick your stop" menus after a route and direction have been selected.

_Example: a particular `route_id` and `direction_id` may have two stops `A` and `B`, ordered such that `A` precedes `B`. This means that there are no trips on this route in this direction that serve stop `B` before stop `A`. It does not guarantee that there any trips that serve both `A` and `B`, becuase some trips may serve one but not the other._
Field Name | GTFS spec | Status | Notes
---------- | -------- | ------ | --------
route_id | Experimental | Included | Linked to routes.txt file.
direction_id | Experimental | Included | Binary value linked to trips.txt file.
stop_id | Experimental | Included | Linked to stops.txt file. 
route_stop_order | Experimental | Included | Orders the stops on trips with this `route_id` and `direction_id` in a way that is ideal for presentation to riders. For a particular `route_id` and `direction_id`, stops with a smaller `route_stop_sort_order` should be displayed first.

### Notes 

- While not directly reflected in the GTFS, please note that the rail routes affected above are now being referred to by SEPTA as its “Metro” network – parallel to SEPTA’s Bus network and Regional Rail network. While these routes will retain their appropriate GTFS route_type, these six lines (13 GTFS routes including all service patterns) will be collectively referenced as “Metro” routes on signage and throughout SEPTA service communication moving forward.  
- Please note the new colors for each of the Metro lines – all except the [B] have been updated to either a different shade ([L], [T], and [M]) or a completely new color ([D] and [G]). These colors are already included in the current GTFS-static feed, but should start to be used as of February.  
- When rendering route names in plain text, it is preferable to use the `route_long_name` followed by the `route_short_name` in brackets: "Board the Norristown High Speed Line [M1] at Villanova." This is to assist riders who may be unfamiliar with the new nomenclature. This recommendation will change in the future. 
- The order of the Subway-Surface Trolleys [T] routes has changed. The existing order (10, 11, 13, 34, 36) is for historical reasons. The new ordering (T1, T2, T3, T4, T5) reflects their relative geographic locations (North to South) rather than historical numbering. Note that Route 15 [G1] has a different letter because it forms a separate "trunk" in the core of the city from the Subway-Surface Trolley [T] routes. 
- The former Broad Street Line (BSL) is being split into three distinct routes: Broad Street Local [B1], Broad Street Express [B2], and Broad-Ridge Spur [B3]. Trips (in trips.txt) have been assigned to the appropriate route. 
- Individual routes should always be referred to with their alpha-numeric name (e.g. B2, T4, G1). However, the letter alone may be used in certain cases to refer to all of the routes on a line: for example, identifying 13th St as a station where all [T] and [L] services may be found. The single letters are not found in the GTFS.  
- Certain stop_name fields are also being updated as part of the Metro transition. Some of these changes have already been made, while additional changes will be reflected in the February GTFS-static feed. These changes include: small consistency updates (e.g. Street --> St), new names to resolve duplicate station names (e.g. Broad-Girard and Front-Girard), and the consolidation of 15th St and City Hall stations into 15th St/City Hall Station. This round of updates does not include any changes to parent/child stop relationships.  
