## Przykładowe zadania:
1. Zwróć dane wszystkich zamkniętych (open) firm (business). Zapytanie powinno zwracać dane z pól: nazwa, adres, gwiazdk (stars)

        db.business.find({open: false},{name: 1, full_address: 1, stars: 1}).pretty()
    `RESULT: `

        {
            "_id" : ObjectId("624b261244ba9b7078636af3"),
            "full_address" : "4156 County Rd B\nMc Farland, WI 53558",
            "name" : "Charter Communications",
            "stars" : 1.5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636af9"),
            "full_address" : "6401 University Ave\nMiddleton, WI 53562",
            "name" : "Crandalls Carryout & Catering",
            "stars" : 4
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636afd"),
            "full_address" : "6230 University Ave\nMiddleton, WI 53562",
            "name" : "Mi Cocina",
            "stars" : 3
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b21"),
            "full_address" : "6625 Century Ave\nMiddleton, WI 53562",
            "name" : "Stamm House At Pheasant Branch",
            "stars" : 2
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b2e"),
            "full_address" : "6661 University Ave\nSte 103\nMiddleton, WI 53562",
            "name" : "Tangles",
            "stars" : 2
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b2f"),
            "full_address" : "1901 Cayuga St\nMiddleton, WI 53562",
            "name" : "Soup Factory",
            "stars" : 3
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b48"),
            "full_address" : "1632 W Main St\nSun Prairie, WI 53590",
            "name" : "Deli Roma",
            "stars" : 4
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b5d"),
            "full_address" : "2910 E Washington Ave\nEken Park\nMadison, WI 53704",
            "name" : "Java Detour",
            "stars" : 4.5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b61"),
            "full_address" : "4120 Monona Dr\nLake Edge\nMadison, WI 53716",
            "name" : "Bongo Video",
            "stars" : 5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b72"),
            "full_address" : "3001 N Sherman Ave\nSherman\nMadison, WI 53704",
            "name" : "Rocky Rococo Pan Style Pizza",
            "stars" : 1.5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b95"),
            "full_address" : "1902 E Johnson St\nEmerson East\nMadison, WI 53704",
            "name" : "Area 51 Vintage Interiors",
            "stars" : 3
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b97"),
            "full_address" : "3729 E Washington Ave\nMayfair Park\nMadison, WI 53704",
            "name" : "Williamson Bikes & Fitness",
            "stars" : 3.5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b99"),
            "full_address" : "1941 Winnebago St\nSchenk - Atwood\nMadison, WI 53704",
            "name" : "Designs By the Bay",
            "stars" : 2.5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636b9d"),
            "full_address" : "1151 N Sherman Ave\nSherman\nMadison, WI 53704",
            "name" : "Dorn True Value Hardware",
            "stars" : 2.5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636ba5"),
            "full_address" : "2044 Atwood Ave\nSchenk - Atwood\nMadison, WI 53704",
            "name" : "Wong's Garden",
            "stars" : 3.5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636be2"),
            "full_address" : "3502 E Washington Ave\nHawthorne\nMadison, WI 53704",
            "name" : "Dimitri's Gyros",
            "stars" : 3.5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636bfa"),
            "full_address" : "4426 E Buckeye Rd\nElvehjem\nMadison, WI 53716",
            "name" : "Poppa Coronofoulos Gyros & Chicago Style Deli",
            "stars" : 4
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636c06"),
            "full_address" : "100 Frost Woods Rd\nMonona, WI 53716",
            "name" : "Rossi's",
            "stars" : 4
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636c0f"),
            "full_address" : "4603 Buckeye Rd\nLake Edge\nMadison, WI 53716",
            "name" : "Groff's Buckeye Barber Shop",
            "stars" : 5
        }
        {
            "_id" : ObjectId("624b261244ba9b7078636c13"),
            "full_address" : "300 Cottage Grove Rd\nEastmorland\nMadison, WI 53716",
            "name" : "Packer Inn",
            "stars" : 3
        }
    

2. Ile miejsc ocenianych na 5 gwiazdek (pole stars kolekcja business) 

        db.business.find({stars: 5}).count()

    `RESULT: ` 5097

3. Zwróć bez potórzeń wszystkie nazwy miast w których znajdują się firmy (business)

        db.business.distinct("city")

`RESULT:`

    [
            "Ahwatukee",
            "Anthem",
            "Apache Junction",
            "Arcadia",
            "Atlanta",
            "Avondale",
            "Black Canyon City",
            "Bonnyrigg",
            "Boulder City",
            "Buckeye",
            "C Las Vegas",
            "Cambridge",
            "Carefree",
            "Casa Grande",
            "Cave Creek",
            "Centennial Hills",
            "Central City Village",
            "Central Henderson",
            "Chandler",
            "Chandler-Gilbert",
            "City of Edinburgh",
            "Clark County",
            "Columbus",
            "Coolidge",
            "Cottage Grove",
            "Cramond",
            "Dalkeith",
            "Dane",
            "De Forest",
            "DeForest",
            "Deforest",
            "Eagan",
            "Edinburgh",
            "El Mirage",
            "Enterprise",
            "Fitchburg",
            "Florence",
            "Fort Kinnaird",
            "Fort McDowell",
            "Fort Mcdowell",
            "Fountain Hills",
            "Fountain Hls",
            "Gila Bend",
            "Gilbert",
            "Glendale",
            "Glendale Az",
            "Gold Canyon",
            "Goldfield",
            "Goodyear",
            "Green Valley",
            "Guadalupe",
            "Heidelberg",
            "Henderson",
            "Henderson ",
            "Henderson (Green  Valley)",
            "Henderson (Stephanie)",
            "Henderson and Las vegas",
            "Henderston",
            "Higley",
            "Inverkeithing",
            "Juniper Green",
            "Kitchener",
            "Lake Las Vegas",
            "Las Vegas",
            "Las Vegas ",
            "Las Vegas East",
            "Las Vegas, NV 89147",
            "Las Vegass",
            "Lasswade",
            "Laveen",
            "Leith",
            "Litchfield Park",
            "Litchfield Park ",
            "Loanhead",
            "London",
            "Madison",
            "Maricopa",
            "Mc Farland",
            "McFarland",
            "Mcfarland",
            "Mesa",
            "Mesa ",
            "Middleton",
            "Midlothian",
            "Monona",
            "Morristown",
            "Musselburgh",
            "N E Las Vegas",
            "N Las Vegas",
            "N W Las Vegas",
            "N. Las Vegas",
            "NELLIS AFB",
            "Nellis AFB",
            "Nellis Afb",
            "Nellis Air Force Base",
            "New River",
            "New Town",
            "New York",
            "Newberry Springs",
            "Newbridge",
            "Newington",
            "North Las Vegas",
            "North Las Vegas ",
            "North Queensferry",
            "North Scottsdale",
            "Old Town",
            "Paradise",
            "Paradise Valley",
            "Penicuik",
            "Peoria",
            "Pheonix",
            "Phoenix",
            "Phoenix ",
            "Phoenix Sky Harbor Center",
            "Portobello",
            "Queen Creek",
            "Queensferry",
            "Ratho",
            "Rio Verde",
            "Rochester",
            "Roslin",
            "Saguaro Lake",
            "Saint Jacobs",
            "San Tan Valley",
            "Scotland",
            "Scottsdale",
            "Scottsdale, Phoenix, Chandler, Gilbert",
            "Sedona",
            "South Gyle",
            "South Las Vegas",
            "South Queensferry",
            "Spring Valley",
            "St Clements",
            "St Jacobs",
            "St. Jacobs",
            "Stanfield",
            "Stockbridge",
            "Stoughton",
            "Straiton",
            "Summerlin",
            "Summerlin South",
            "Sun City",
            "Sun City Anthem",
            "Sun City West",
            "Sun Lakes",
            "Sun Prairie",
            "Sunrise",
            "Sunrise Manor",
            "Surprise",
            "Surprise Crossing",
            "Tempe",
            "Tolleson",
            "Tonopah",
            "Tonto Basin",
            "Tortilla Flat",
            "Trempealeau",
            "Verona",
            "Victoria Park",
            "W Henderson",
            "W Spring Valley",
            "W Summerlin",
            "Waddell",
            "Water of Leith",
            "Waterloo",
            "Waunakee",
            "Whitney",
            "Wickenburg",
            "Windsor",
            "Wittmann",
            "Woolwich",
            "Youngtown",
            "chandler"
    ]

4.  Ile każda firma otrzymało wskazówek (tip) w 2012. Wynik posortuj według liczby wskazówek
(tip). 

        db.tip.aggregate(
        [
            {$match:{"date":/2012/}},
            {$group : {_id:"$business_id", count:{$sum:1}}},
            {$sort:{"count":1}}
        ]
        )

`RESULTS:`

    { "_id" : "y9g-_Em3ISPaimip7Ywavg", "count" : 1 }
    { "_id" : "_IPUEiZFc8vzsXp-BSlpIA", "count" : 1 }
    { "_id" : "YEW6ExhHpp650wy-OeOmrA", "count" : 1 }
    { "_id" : "pSYCSXgabSKKJrIEJG-FLQ", "count" : 1 }
    { "_id" : "ASsdxZQCYX39MwkNazB8bA", "count" : 1 }
    { "_id" : "NqbkQOyymWktiq5ulrl2BA", "count" : 1 }
    { "_id" : "CPZQjiHBEh_4PonvdFO1Hw", "count" : 1 }
    { "_id" : "SwIE90OE0A4ztIu1sFOz3A", "count" : 1 }
    { "_id" : "eM_xhUeM4gh6Emt4lfwz0w", "count" : 1 }
    { "_id" : "rb8rRrH9bcb123-2Qaw3_Q", "count" : 1 }
    { "_id" : "nHQ11YXvzL8awYoF-uD16A", "count" : 1 }
    { "_id" : "3rFTT43tQg992no381rVvQ", "count" : 1 }
    { "_id" : "hf-9dAwfK0uBuScm3pjVOQ", "count" : 1 }
    { "_id" : "rDiaO12WX_HaoRA_Y9FbJA", "count" : 1 }
    { "_id" : "Rk-axrNaCJ2D2iNW--PkQg", "count" : 1 }
    { "_id" : "qK_nxiXCxjIP8Hd659bhvA", "count" : 1 }
    { "_id" : "CQRYL_4Mu3215d1F_C0Qpg", "count" : 1 }
    { "_id" : "LJg8ll83Nio0kiHcAEdRxA", "count" : 1 }
    { "_id" : "1UydNTqQQ-qo8l9JTg_b9w", "count" : 1 }
    { "_id" : "Zt8AwvVw9F6Dn6Q9LXz4xw", "count" : 1 }