# Address Scanner With Maps

A mobile web app for parcel delivery drivers. Scan the QR code on a parcel label, and the delivery address is read off it, placed on a map, and added to your run.

**Open it here: [revaex.github.io/Address-Scanner-With-Maps](https://revaex.github.io/Address-Scanner-With-Maps/)**

Built for a StarTrack contract driver in Melbourne who wanted something faster than typing every address into Google Maps. It is free to use, needs no account, and keeps everything on your own phone.

---

## Getting started

1. Open the link above on your phone. **Chrome on Android** or **Safari on iPhone**.
2. Add it to your home screen so it opens like a normal app — *Share → Add to Home Screen* on iPhone, *⋮ → Add to Home screen* on Android.
3. Allow the camera when it asks. It is only used to read barcodes.
4. Allow location if you want the route worked out from where you are.

Nothing to install, no sign-up, no cost.

## How you use it

**Loading the van.** Tap **Start scanning** and point the camera at the QR code on each label. The address is read off the code and the parcel appears on the map. By default the screen jumps down to the map and centres on the parcel you just added, so you can see where it is going before you decide where to put it in the van.

Parcel numbers follow the order you scan, and that never changes — parcel 4 is the fourth box you loaded, always. That matters, because it is how you find the right box later without digging.

**On the road.** The map shows every stop with the address written beside the pin. Tap a pin for **Navigate**, which hands off to Google Maps, or **Done** when it is delivered. The list view does the same thing.

**Working out an order.** Tap **Suggest an order** and it works out a shorter run, starting from where you are and finishing at your depot. It never reorders your list — it shows the suggested order as a separate view, with the parcel number on each stop so you still know which box to grab. There is also a load order panel and a re-sort helper that tells you only the parcels that are genuinely out of place.

## What it does

**Reading labels**
- Scans QR codes with the camera, tuned for the dense codes on courier labels
- Reads a photo of a label if the code will not scan live
- Reads the *printed address* with the camera when there is no usable code at all
- Understands StarTrack and Shippit payloads, JSON and tagged formats, and will hunt for an Australian address in anything else
- Tells you honestly when it cannot read something instead of inventing an address
- Knows the difference between the same parcel scanned twice and a second parcel for the same address

**Addresses and the map**
- Type an address any way you like — `11/20 Toorak Ave`, `U11/20 Toorak Avenue Croydon`, no suburb, no postcode. Predictive suggestions as you type, on every address box
- Flags a stop as a rough placement when it can only find the street and not the number, rather than pretending it is exact
- Drag a pin, or tap the map, to put a stop exactly where you know it is. Pins you place by hand are kept and never moved
- Tap the map to add a stop that has no label at all
- Addresses written beside every pin, a full-screen map for driving, and a live GPS dot

**Running the round**
- Route optimisation by straight line, road distance or road time
- Hands off to Google Maps in legs, so it works with Android Auto
- Load order and re-sort helper
- Marks off deliveries with the time, and remembers the order you actually delivered in
- Learns which addresses you tend to deliver back to back and nudges future suggestions — capped, so it can never override real geography

**Keeping a record**
- Saved runs viewer on the phone
- Export to a spreadsheet, with delivery times
- Backup and restore to move everything to another phone

**Settings**
Choose what happens after each scan (jump to the map, open the stop card, or stay put and keep scanning), whether the screen stays awake, whether it buzzes, and more.

## Your data

Everything stays in your browser on your phone. There is no server, no account, no analytics, and nothing is uploaded anywhere.

That also means it is only as safe as your browser. Clearing your browsing data will erase it, and phones sometimes drop storage from sites left unused for a long time. **If your runs matter to you, use Export or Backup in the Delivery history panel.**

## Good to know

- The camera only works over `https://`, which the link above is. It will not work from a file opened directly off your phone.
- Geocoding and routing use free public services. They are rate limited and occasionally go down. Everything has a fallback, but on a bad day an address may take a moment or fail to place — you can always drop the pin yourself.
- Live traffic routing needs a paid Google key, so it is not included. Road time is the closest free equivalent.
- The address reader downloads a language pack the first time you use it, so the first read is slow and the rest are quick.
- Tap **Load the latest** at the bottom of the page if you think you are on an old version. The build number is shown next to it.

## For developers

One `index.html` file. No build step, no bundler, no dependencies in the shipped file — libraries load from CDNs. Hosted on GitHub Pages.

```
index.html      the whole app
PROJECT.md      architecture, constraints and working practice — read this first
test.js         test suite, 798 tests
harness.js      loads the real index.html in jsdom with the browser bits stubbed
payloads.json   QR payloads decoded from photographs of real labels
```

Running the tests:

```bash
npm install jsdom
cp index.html app.html
node test.js        # one line per section
node test.js -v     # every assertion
```

The suite runs against the actual shipped file rather than a copy, so it exercises the code that really ships.

Third-party services, all free and keyless: Leaflet and OpenStreetMap tiles, Html5Qrcode, Photon and Nominatim for geocoding, OSRM for routing, Tesseract.js for reading printed addresses.

If you are picking this up, read `PROJECT.md` before changing anything. Two rules matter most: **it must stay free** — no paid APIs or keys — and **never reorder the scan list**, because the parcel numbers match the physical stack in the van.

## Credit

Built with [Claude](https://claude.ai), shaped by a real driver's feedback after real days on the road.
