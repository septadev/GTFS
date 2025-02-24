# SEPTA Metro - GTFS Feed 

#### About this document   

This document is intended to help developers prepare for SEPTA's transition to its new "Metro" nomenclature. It describes how SEPTA's updated GTFS-static feed, planned to launch with the February 2025 schedule change, differs from its current feed. (https://github.com/septadev/GTFS/releases/tag/v202502240). This document *is* a guide to anticipated changes in SEPTA's GTFS-static feed. 

It *is not*: 

- A comprehensive guide to SEPTA's GTFS feeds or [GTFS itself] (https://gtfs.org/schedule/) 
- A comprehensive guide to SEPTA's upcoming Metro nomenclature and wayfinding overhaul. More info on the changes can be found at www.septa.org/metro 
- A guarantee that SEPTA will provide data in any particular format (though we will try our best) 
- A [license agreement] (https://wwww.septa.org/license-agreement/)  

## routes.txt 

The route names of SEPTA's heavy rail (subway/elevated) and light rail (trolley) routes, and certain bus routes are [changing](https://wwww.septa.org/metro/letters-colors-symbols/). In GTFS, the new nomenclature will be in the `route_short_name` field, while the old nomenclature remains in the `route_long_name`. The `route_id` field will be updated to match the `route_short_name` field, as is current practice. Physical signage will be replaced throughout the system over the coming months/years, expected to be completed in 2026. SEPTA’s app and website will be displaying both new and old nomenclature side-by-side to support riders through this transition. 

| Current route_id | Current route_short_name | Current route_long_name             | - | New route_id | New route_short_name | New route_long_name                 | 
| ---------------- | ------------------------ | ----------------------------------- | - | ------------ | -------------------- | ----------------------------------- |
| 10               | 10                       | Route 10                            | - | T1           | T1                   | Route 10                            |  
| 11               | 11                       | Route 11                            | - | T4           | T4                   | Route 11                            | 
| 13               | 13                       | Route 13                            | - | T3           | T3                   | Route 13                            | 
| 15               | 15                       | Route 15                            | - | G1           | G1                   | Route 15                            | 
| 34               | 34                       | Route 34                            | - | T2           | T2                   | Route 34                            | 
| 36               | 36                       | Route 36                            | - | T5           | T5                   | Route 36                            | 
| 101              | 101                      | Route 101                           | - | D1           | D1                   | Route 101                           |
| 102              | 102                      | Route 102                           | - | D2           | D2                   | Route 102                           |
| BSL              | BSL                      | Broad Street Line                   | - | B1           | B1                   | Broad Street Line Local             |
| BSL              | BSL                      | Broad Street Line                   | - | B2           | B2                   | Broad Street Line Express           |
| BSL              | BSL                      | Broad Street Line                   | - | B3           | B3                   | Broad-Ridge Spur                    |
| MFL              | MFL                      | Market-Frankford Lin                | - | L1           | L1                   | Market-Frankford Line               |
| NHSL             | NHSL                     | Norristown High Speed Line          | - | M1           | M1                   | Norristown High Speed Line Local             |
| G                | G                        | Overbk/LankMC to ColCom/FdDstCtr    | - | 63           | 63                   | G - Lanknau/Overbrk to ColCom/FdCtr |
| H                | H                        | Broad-Erie to Cheltenham-Ogontz-H   | - | 71           | 71                   | H - Broad-Erie to Cheltenham-Ogontz |
| J                | J                        | Chelten-Wisshkn to Richmond-Orthodx | - | 41           | 41                   | J - Cheltn-Wsshkn to Richmnd-Orthdx |
| K                | K                        | Ridge-Midvale to Arrott TC          | - | K            | K                    | Ridge-Midvale to Arrott TC          |
| L                | L                        | ChestnutHill/PlymouthMtgMall to OTC | - | 51           | 51                   | L - PlymthMtg/ChestntHl to Olney TC |
| R                | R                        | Henry-Mid or WissTC to FrankfordTC  | - | 82           | 82                   | R - Wissahckn TC/Henry-Midvl to FTC |
| XH               | XH                       | Broad-Erie to Cheltenham-Ogontz-XH  | - | 81           | 81                   | XH - Broad-Erie to Cheltenham-Ogntz |

Note that in addition to the Metro routes switching to Letter-Number pairs, bus routes that formerly used letter(s) are switching to numbers only. This is so that there are no duplicates with the new Metro letters, and so that moving forward, letters always refer to Metro routes and numbers always refer to Bus routes. Specifically G, H, J, L, R, and XH are changing to numbers. Bus route K will remain “K” until it is discontinued (planned for 2025). 

Additionally, trolley replacement routes will be added over time as they are needed. These replacement routes are temporary 1:1 replacements of trolleys with buses due to roadwork or other obstacles to trolleys that buses can navigate around. Our trolley network is largely street-running in mixed traffic, so riders will not experience a major change in boarding locations, frequencies, or amenities. Once added, they will not be removed from future feeds, even if no trips are assigned to those routes. They will have a route_id consisting of the route_id of the route they are replacing, followed by a space and the letters “BUS” (for example, route_id “T5 BUS” indicates a bus-operated service replaceing part or all of the T5 route, which is ordinarily a trolley). The route_short_name will also be “T5 BUS” (for example), and the route_long_name will be the same as the service being replaced. Please note: the bus replacement service will carry the route_type of “0” (which indicates a trolley), not “3” (which would indicate a bus). This is an intentional mismatch with the actual type of the vehicle on the street, and is done so that these temporary replacement services will be categorized as “Metro” services in our own tool and third party tools. 

### Notes 

- While not directly reflected in the GTFS, please note that the rail routes affected above are now being referred to by SEPTA as its “Metro” network – parallel to SEPTA’s Bus network and Regional Rail network. While these routes will retain their appropriate GTFS route_type, these six lines (13 GTFS routes including all service patterns) will be collectively referenced as “Metro” routes on signage and throughout SEPTA service communication moving forward.  
- Please note the new colors for each of the Metro lines – all except the [B] have been updated to either a different shade ([L], [T], and [M]) or a completely new color ([D] and [G]). These colors are already included in the current GTFS-static feed, but should start to be used as of February.  
- When rendering route names in plain text, it is preferable to use the `route_long_name` followed by the `route_short_name` in brackets: "Board the Norristown High Speed Line [M1] at Villanova." This is to assist riders who may be unfamiliar with the new nomenclature. This recommendation will change in the future. 
- The order of the Subway-Surface Trolleys [T] routes has changed. The existing order (10, 11, 13, 34, 36) is for historical reasons. The new ordering (T1, T2, T3, T4, T5) reflects their relative geographic locations (North to South) rather than historical numbering. Note that Route 15 [G1] has a different letter because it forms a separate "trunk" in the core of the city from the Subway-Surface Trolley [T] routes. 
- The former Broad Street Line (BSL) is being split into three distinct routes: Broad Street Local [B1], Broad Street Express [B2], and Broad-Ridge Spur [B3]. Trips (in trips.txt) have been assigned to the appropriate route. 
- Individual routes should always be referred to with their alpha-numeric name (e.g. B2, T4, G1). However, the letter alone may be used in certain cases to refer to all of the routes on a line: for example, identifying 13th St as a station where all [T] and [L] services may be found. The single letters are not found in the GTFS.  
- Certain stop_name fields are also being updated as part of the Metro transition. Some of these changes have already been made, while additional changes will be reflected in the February GTFS-static feed. These changes include: small consistency updates (e.g. Street --> St), new names to resolve duplicate station names (e.g. Broad-Girard and Front-Girard), and the consolidation of 15th St and City Hall stations into 15th St/City Hall Station. This round of updates does not include any changes to parent/child stop relationships.  
