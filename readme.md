# What is this?

This is a javascript/typescript library for using google maps with custom markers and legend. The library is not complete and need polishing. Not everything can be configured outside of the class with functions etc. But its fits my basic needs.

# How to install

this package supports bower so it can be installed using the `bower install GMap` command. It will then automatically direct to a minified ES5 version of the library. ES3 and ES6 are also available. If you don't use bower also install [js-marker-clusterer][js-marker-clusterer]
manually (this is automatically done by bower). ~~It is also needed to past `<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=_YOUR_API_KEY_"/>` in your header. (ideally i would javascript load it but that [didn't work out][stackOverflow])~~

# Example.

Please see [test html page][test]
```html
<!DOCTYPE html>
<html>

<head>
    <title>test page</title>
    <!-- you should get markercluster from https://github.com/googlemaps/js-marker-clusterer -->
    <script type="text/javascript" src="markerclusterer.js"></script>
    <script type="text/javascript" src="../dist/Gmap.es5.min.js"></script>
    <style media="screen">
        div#mapObject {
            width: 100%;
            height: 50vh;
        }
    </style>
</head>
<body>
    <div id="mapObject"></div>
    <script type="text/javascript">
    //demo script
    var apiKey = prompt("Please enter your google maps api key", "_YOUR_API_KEY_");
    var map;
    function initMap() {
        // select #mapObject
        var mapObject = document.querySelector("#mapObject");
        // create map
        map = new GMap(window.apiKey, mapObject, {
                    center: {
                        lat: 39.3064901,
                        lng: 23.1190815
                    },
                    zoom: 10
                        // callback
                }, function() {
                    // addLegendaItems name, slug, imageUrl
                    this.addLegendaItem("Cultuur", "culture", "https://cdn4.iconfinder.com/data/icons/banking-and-finance/500/bank-building-48.png");
                    this.addLegendaItem("Natuur", "nature", "https://cdn2.iconfinder.com/data/icons/circle-icons-1/64/flower-48.png");
                    this.addLegendaItem("Bergen & stenen", "mountain", "https://cdn0.iconfinder.com/data/icons/citycons/150/Citycons_mountain-48.png");
                    this.addLegendaItem("Strand & Zee", "beach", "https://cdn0.iconfinder.com/data/icons/kameleon-free-pack-rounded/110/Beach-48.png");
                    this.addLegendaItem("Eten", "restaurant", "https://cdn0.iconfinder.com/data/icons/kameleon-free-pack-rounded/110/Food-Dome-48.png");
                    this.addLegendaItem("Activiteiten", "activity", "https://cdn2.iconfinder.com/data/icons/circle-icons-1/64/calendar-48.png");
                    this.addLegendaItem("Winkels", "shop", "https://cdn1.iconfinder.com/data/icons/ecommerce-free/96/Cart-48.png");
                    this.addLegendaItem("Hotel", "hotel", "https://cdn4.iconfinder.com/data/icons/hotel-icons-1/744/sleeping_hotel_bed_hostel-48.png");
                    this.addLegendaItem("Dorpen & Steden", "village", "https://cdn0.iconfinder.com/data/icons/citycons/150/Citycons_building-48.png");
                    this.addLegendaItem("Standaard", "default", "https://cdn0.iconfinder.com/data/icons/social-networks-and-media-flat-icons/136/Social_Media_Socialmedia_network_share_socialnetwork_network-14-48.png");
                    // add markers
                    //{lat: float, lng: float}, title, content, categorieSlug, link
                    this.makeMarker({
                        lat: 39.41318832104817,
                        lng: 23.16275847934571
                    }, 'test shop 2', '', 'activity', 'http://www.example.com/');
                    this.makeMarker({
                        lat: 39.41439382110282,
                        lng: 23.164036415869077
                    }, 'test shop', '', 'shop', 'http://www.example.com/');
                    this.makeMarker({
                        lat: 39.41227185069104,
                        lng: 23.16575302963861
                    }, 'test village', '', 'village', 'http://www.example.com/');
                    this.makeMarker({
                        lat: 39.41479168336505,
                        lng: 23.16146149521478
                    }, 'test  5', '', 'culture', 'http://www.example.com/');
                    this.makeMarker({
                        lat: 39.417311424965305,
                        lng: 23.15871491318353
                    }, 'test 4', '', 'mountain', 'http://www.example.com/');
                    this.makeMarker({
                        lat: 39.41426119984417,
                        lng: 23.158028267675718
                    }, 'test 3', '', 'beach', 'http://www.example.com/');
                    this.makeMarker({
                        lat: 39.4009978,
                        lng: 23.1645514
                    }, 'test 2', '', 'nature', 'http://www.example.com/');
                    this.makeMarker({
                        lat: 39.2701026401936,
                        lng: 23.241548328124964
                    }, 'test sight', '', 'restaurant', 'http://www.example.com/');
                    this.makeMarker({
                            lat: 39.390234,
                            lng: 22.9974447
                        }, 'Agrosweet Woman&#8217;s Association in Zagora',
                        'Ζαγορά, σ’ αυτόν τον τόπο, το Νοέμβριο του 1993,  ιδρύθηκε ο Γυναικείος Αγροτοτουριστικός Συνεταιρισμός Ζαγοράς, ο μοναδικός Γυναικείος Συνεταιρισμός της Μαγνησίας, από 50 γυναίκες      που θέλησαν να αξιοποιήσουν τις παραδόσεις τους και να προσφέρουν υπηρεσίες όχι στεγνά τουριστικές, αλλά δουλειά με κέφι, μεράκι και ποιότητα. Το Πήλιο, από τα πιο όμορφα ελληνικά βουνά, γνωστό από &hellip;',
                        'default', 'http://www.example.com/');
                    this.makeMarker({
                            lat: 39.4416384,
                            lng: 23.1028193
                        }, 'Saint George Church in Zagora',
                        'Ο Ιερός Ναός Αγίου Γεωργίου Ζαγοράς όπως διαπιστώνουμε εξ&#8217; αναγλύφου μαρμάρινης πλάκας που είναι εντοιχισμένη στο εξωτερικό μέρος της ανατολικής πλευράς του Ναού δηλώνει: Ανηγέρθη εκ βάθρων την 14η Μαρτίου 1765 δια προτροπής του πρώην Κωνσταντινουπόλεως Πατριάρχου Καλλινίκου  και κοινής βοηθείας συνδρομής των ενοριτών και λοιπών εγχωρίων, επί των ημερών του Αγίου Δημητριάδος Γρηγορίου. Επίσης &hellip;',
                        'culture', 'http://www.example.com/');
                    this.makeMarker({
                            lat: 39.3876414,
                            lng: 23.174311
                        }, 'Irthe ke Edese',
                        'Στο &#8220;Ήρθε και Έδεσε&#8221; μπορεί να απολαύσει κανείς πεντανόστιμο φαγητό, σε ένα πολύ όμορφο περιβάλλον. Η τοποθεσία του μοναδική, αφού είναι εύκολα προσβάσιμη από τα χωριά του Πηλίου και μόλις λίγα μέτρα από τη θάλασσα. Ιδανικό για ένα ωραίο δείπνο αλλά και για ένα γρήγορο φαγητό μετά το μπάνιο.Βασικός λόγος να το επισκεφτείς είναι η &hellip;',
                        'restaurant', 'http://www.example.com/');
                    this.makeMarker({
                        lat: 39.41044669370065,
                        lng: 23.16603854498294
                    }, 'Agapitos Villas', 'Price from 45€ per person in Double Room (Low Season) Price from 755€ per person in Double Room (High Season)', 'hotel', 'http://www.example.com/');
                });
            }
            initMap();

    </script>
</body>

</html>
```
Looks something like this

![sample img][img]
# Reference

`constructor(apiKey: string, target: any, mapOptions: any, callback: any)` Build google map, Returns map object

`.map` google map object.

`.markers` array of all the markers.

`.zoom` var, set zoom level.

`.center` var, set center of map {lat: float, lng: float}

`.mapType` var, setMapTypeId

`.getCor(adress: string)` Returns coordinates of a place - Return {lat: float, lng: float}

`.marker(slug: string): any` returns marker of categorie, use slug

`.makeMarker({lat, lng}: { lat: number, lng: number }, title: string, content: string, categorie: string, link: string): any` Create a marker on map, Returns marker object

`.toggleCat(categorie: string): void` Hide or display a categorie

`.getAllMarkers(): any[]` get all the markers in a single flat array.

`addLegendaItem(name: string, slug: string, iconUrl: string): void` Make new legenda item


[stackOverflow]: http://stackoverflow.com/questions/39975325/google-maps-js-api-not-showing
[js-marker-clusterer]: https://github.com/googlemaps/js-marker-clusterer
[test]: test/test.html
[img]: http://i.imgur.com/Swtl0Dx.png
