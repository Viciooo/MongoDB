# 9. Modelowanie danych
- Zaproponuj strukturę bazy danych dla wybranego/przykładowego zagadnienia/problemu
- Należy wybrać jedno zagadnienie/problem (A lub B) - `ja wybrałem A`

## Przykład A
- Wykładowcy, przedmioty, studenci, oceny
- Wykładowcy prowadzą zajęcia z poszczególnych przedmiotów
- Studenci uczęszczają na zajęcia
- Wykładowcy wystawiają oceny studentom
- Studenci oceniają zajęcia

Warto zaproponować/rozważyć różne warianty struktury bazy danych i dokumentów w 
poszczególnych kolekcjach oraz przeprowadzić dyskusję każdego wariantu (wskazać wady i zalety każdego z wariantów)

W sprawozdaniu należy zamieścić przykładowe dokumenty w formacie JSON (wraz z 
odpowiednim komentarzem opisującym strukturę dokumentów) oraz polecenia ilustrujące wykonanie przykładowych operacji na danych

Do sprawozdania należy kompletny zrzut wykonanych/przygotowanych baz danych (taki zrzut można wykonać np. za pomocą poleceń mongoexport, bsondump …). Do sprawozdania należy dołączyć plik zip.

## Solutions
- I creating & switching to db:
    
        use University

- Adding collections:

        db.createCollection("students")
        db.createCollection("teachers")

### Inserting students:
    - paste it into mongoshell

            students = [
            {
                "firstname": "Mike",
                "lastname": "Tv",
                "university-mail": "MikeTv@student.agh.edu.pl",
                "phone": 987654321,
                "gender": "m",
                "actively-studing": true,
                "courses": ["asddDASDD12","KLjdsf12jnf"]
            },
            {
                "firstname": "Kate",
                "lastname": "Li",
                "university-mail": "KateLi@student.agh.edu.pl",
                "phone": 666666666,
                "gender": "f",
                "actively-studing": true,
                "courses": ["asddDASDD12","KLjdsf12jnf"]
            },
            {
                "firstname": "Tom",
                "lastname": "Holandt",
                "university-mail": "TomHolandt@student.agh.edu.pl",
                "phone": 111111111,
                "gender": "m",
                "actively-studing": false,
                "courses": ["asddDASDD12"]
            }
            ]
    - then use:

            db.student.insertMany(students)

- Checking if everything is fine:

        db.student.find().pretty()
    
    `RESULT:`

        {
                "_id" : ObjectId("624d7f93163e2b1d4f15e11b"),
                "firstname" : "Mike",
                "lastname" : "Tv",
                "university-mail" : "MikeTv@student.agh.edu.pl",
                "phone" : 987654321,
                "gender" : "m",
                "actively-studing" : true,
                "courses" : [
                        "asddDASDD12",
                        "KLjdsf12jnf"
                ]
        }
        {
                "_id" : ObjectId("624d7f93163e2b1d4f15e11c"),
                "firstname" : "Kate",
                "lastname" : "Li",
                "university-mail" : "KateLi@student.agh.edu.pl",
                "phone" : 666666666,
                "gender" : "f",
                "actively-studing" : true,
                "courses" : [
                        "asddDASDD12",
                        "KLjdsf12jnf"
                ]
        }
        {
                "_id" : ObjectId("624d7f93163e2b1d4f15e11d"),
                "firstname" : "Tom",
                "lastname" : "Holandt",
                "university-mail" : "TomHolandt@student.agh.edu.pl",
                "phone" : 111111111,
                "gender" : "m",
                "actively-studing" : false,
                "courses" : [
                        "asddDASDD12"
                ]
        }   
    
### Inserting teachers
Works same like adding students but I add only one teacher now.

        Joe = {
        "firstname": "John",
        "lastname": "Doe",
        "university-mail": "JohnDoe@agh.edu.pl",
        "phone": 123456789,
        "gender": "m",
        "actively-teaching": true,
        "courses": 
        {
            "Mathematics": {
                "course-id": "asddDASDD12",
                "ECTS": "4",
                "course-ratings": [7,2],
                "enrolled-students": [
                    {
                        "id": ObjectId("624d7f93163e2b1d4f15e11b"),
                        "marks": [
                            {
                                "name":"quiz-1",
                                "teacher-comment":"Not to shabby",
                                "mark": 3
                            },
                            {
                                "name":"big-test-1",
                                "teacher-comment":"OK",
                                "mark": 5
                            }
                        ],
                        "final-mark": 0
                    },
                    {
                        "id": ObjectId("624d7f93163e2b1d4f15e11c"),
                        "marks": [
                            {
                                "name":"quiz-1",
                                "teacher-comment":"Pretty bad",
                                "mark": 2
                            },
                            {
                                "name":"big-test-1",
                                "teacher-comment":"OK",
                                "mark": 3
                            }
                        ],
                        "final-mark": 0
                    }
                ],
                "classes": [
                    {
                        "name": "Integrals",
                        "place": "D-17",
                        "duration": 1.5,
                        "date": "2022-04-03T16:00:00Z",
                        "status": "happened",
                        "participants-ids": [ObjectId("624d7f93163e2b1d4f15e11b"),ObjectId("624d7f93163e2b1d4f15e11c")]  
                    },
                    {
                        "name": "Derivatives",
                        "place": "https://teams.microsoft.com/meeting-code",
                        "duration": 3,
                        "date": "2022-04-10T12:00:00Z",
                        "status": "planned",
                        "participants-ids": []  
                    }
                ]
            
            },
            "Phisics": {
                "course-id": "KLjdsf12jnf",
                "ECTS": "100",
                "course-ratings": [10,1],
                "enrolled-students": 
                    [
                        {
                        "id": ObjectId("624d7f93163e2b1d4f15e11d"),
                        "marks": [
                            {
                                "name":"quiz-1",
                                "teacher-comment":"Not to shabby",
                                "mark": 1
                            },
                            {
                                "name":"big-test-1",
                                "teacher-comment":"OK",
                                "mark": 5
                            }
                        ],
                        "final-mark": 0
                        },
                        {
                            "id": ObjectId("624d7f93163e2b1d4f15e11c"),
                            "marks": [
                                {
                                    "name":"quiz-1",
                                    "teacher-comment":"OK",
                                    "mark": 3
                                },
                                {
                                    "name":"big-test-1",
                                    "teacher-comment":"OK",
                                    "mark": 3
                                }
                            ],
                            "final-mark": 0
                        }
                    ],
                "classes": [
                    {
                        "name": "wHy pHysiCS Is aWEsome",
                        "place": "D-17",
                        "duration": 6,
                        "date": "2021-04-03T16:00:00Z",
                        "status": "canceled",
                        "participants-ids": []  
                    }
                ]
            
            }
        } 
    }

---

    db.teachers.insert(Joe)

## Testing the model
`TODO`

## Pros and cons
`TODO`

## Alternative model
`TODO`
