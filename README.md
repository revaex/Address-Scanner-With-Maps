# Address Scanner With Maps

A mobile web app for parcel delivery. Scan the QR code on a label and the address is read off it, placed on a map, and added to your run.

**[revaex.github.io/Address-Scanner-With-Maps](https://revaex.github.io/Address-Scanner-With-Maps/)**

Free, no account, no server. Everything stays on your phone.

## Getting started

Open the link on your phone in Chrome or Safari, add it to your home screen, and allow the camera when asked.

## What it does

**Scanning** — reads QR codes with the camera, reads a photo of a label, and reads the printed address when there is no usable code. Handles common courier label formats and says so honestly when it cannot read one.

**Addresses** — type them any way you like, with predictive suggestions. Flags a stop when it can only find the street and not the number. Drag a pin, or tap the map, to place a stop exactly where you know it is.

**The run** — every stop on a map with its address beside the pin, a live GPS dot, and a full-screen map for driving. Route optimisation by distance or driving time, then hands off to Google Maps in legs. Load order and a re-sort helper.

**Delivery records** — mark stops delivered with the time, add a note and a photo at the door, and generate a report for any date range that you can email or print to PDF. Also exports to a spreadsheet.

**Settings** — choose what happens after each scan, whether the screen stays awake, how pins are coloured, and more.

## Your data

Everything is stored in your browser on your phone. Nothing is uploaded anywhere. Clearing your browsing data will erase it, so use Export or Backup if your records matter.


Libraries used, all free and keyless: Leaflet with OpenStreetMap tiles, Html5Qrcode, Photon and Nominatim for geocoding, OSRM for routing, Tesseract.js for reading printed addresses.

Read `PROJECT.md` before changing anything. Two rules matter most: it must stay free, with no paid APIs or keys, and the scan list must never be reordered, because parcel numbers match the physical order in the van.
