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

### Getting activly studing students:

        > db.student.find({"actively-studing": true}).pretty()
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

### Getting marks in Mathematics Course of student and his fellow students

        db.student.aggregate([{
            $lookup: {
                from: "teachers", localField: "_id", foreignField: "courses.Mathematics.enrolled-students.id", as: "teachers"
            }
        }, {$project: {"firstname": 1, "teachers.courses.Mathematics.enrolled-students": 1}}]).pretty()

`RESULT:`

        "_id":ObjectId("624d7f93163e2b1d4f15e11b"), 
        "firstname":"Mike", 
        "teachers": [{
            "courses": {
                "Mathematics": {
                    "enrolled-students": [{
                        "id": ObjectId("624d7f93163e2b1d4f15e11b"), "marks": [{
                            "name": "quiz-1", "teacher-comment": "Not to shabby", "mark": 3
                        }, {
                            "name": "big-test-1", "teacher-comment": "OK", "mark": 5
                        }], "final-mark": 0
                    }, {
                        "id": ObjectId("624d7f93163e2b1d4f15e11c"), "marks": [{
                            "name": "quiz-1", "teacher-comment": "Pretty bad", "mark": 2
                        }, {
                            "name": "big-test-1", "teacher-comment": "OK", "mark": 3
                        }], "final-mark": 0
                    }]
                }
            }
        }]
        }
        {
            "_id": ObjectId("624d7f93163e2b1d4f15e11c"), 
            "firstname":"Kate", 
            "teachers":
            [{
                "courses": {
                    "Mathematics": {
                        "enrolled-students": [{
                            "id": ObjectId("624d7f93163e2b1d4f15e11b"), "marks": [{
                                "name": "quiz-1", "teacher-comment": "Not to shabby", "mark": 3
                            }, {
                                "name": "big-test-1", "teacher-comment": "OK", "mark": 5
                            }], "final-mark": 0
                        }, {
                            "id": ObjectId("624d7f93163e2b1d4f15e11c"), "marks": [{
                                "name": "quiz-1", "teacher-comment": "Pretty bad", "mark": 2
                            }, {
                                "name": "big-test-1", "teacher-comment": "OK", "mark": 3
                            }], "final-mark": 0
                        }]
                    }
                }
            }]
        }
        {
            "_id": ObjectId("624d7f93163e2b1d4f15e11d"), 
            "firstname":"Tom",
            "teachers":[]
        }


## Pros
- easy and fast access for the teacher 
- embedded structure in the spirit of MongoDB (instead of multi-table structue of relational DB's)

## Cons
- getting marks of specific student is really awkward
- queries will be more complicated 

## Alternative model
I personally would prefer something simpler and less embeded, having at least 3 tables:

- students
- teachers
- courses

### Getting student marks from Math for each student:

        db.students.aggregate([
            {$lookup: {from: "courses", localField: "courses.course_id", foreignField: "_id", as: "c"}}, 
            {$project: {"firstname": 1, "c.name": 1,"c.ECTS":1,"courses.marks":1,"courses.final-mark":1}},
        ]).pretty()

`RESULT:`

                {
                "_id" : ObjectId("6254263c276fac157e0efb69"),
                "firstname" : "Mike",
                "courses" : [
                        {
                                "marks" : [
                                        {
                                                "name" : "quiz-1",
                                                "teacher-comment" : "Not to shabby",
                                                "mark" : 3
                                        },
                                        {
                                                "name" : "big-test-1",
                                                "teacher-comment" : "OK",
                                                "mark" : 5
                                        }
                                ],
                                "final-mark" : 4
                        },
                        {
                                "marks" : [
                                        {
                                                "name" : "quiz-1",
                                                "teacher-comment" : "Not to shabby",
                                                "mark" : 1
                                        },
                                        {
                                                "name" : "big-test-1",
                                                "teacher-comment" : "OK",
                                                "mark" : 5
                                        }
                                ],
                                "final-mark" : 2
                        }
                ],
                "c" : [
                        {
                                "name" : "Mathematics",
                                "ECTS" : "4"
                        },
                        {
                                "name" : "Physics",
                                "ECTS" : "100"
                        }
                ]
        }
        {
                "_id" : ObjectId("6254263c276fac157e0efb6a"),
                "firstname" : "Kate",
                "courses" : [
                        {
                                "marks" : [
                                        {
                                                "name" : "quiz-1",
                                                "teacher-comment" : "Pretty bad",
                                                "mark" : 2
                                        },
                                        {
                                                "name" : "big-test-1",
                                                "teacher-comment" : "OK",
                                                "mark" : 3
                                        }
                                ],
                                "final-mark" : 3
                        },
                        {
                                "marks" : [
                                        {
                                                "name" : "quiz-1",
                                                "teacher-comment" : "Not to shabby",
                                                "mark" : 1
                                        },
                                        {
                                                "name" : "big-test-1",
                                                "teacher-comment" : "OK",
                                                "mark" : 5
                                        }
                                ],
                                "final-mark" : 2
                        }
                ],
                "c" : [
                        {
                                "name" : "Mathematics",
                                "ECTS" : "4"
                        },
                        {
                                "name" : "Physics",
                                "ECTS" : "100"
                        }
                ]
        }
        {
                "_id" : ObjectId("6254263c276fac157e0efb6b"),
                "firstname" : "Tom",
                "courses" : [
                        {
                                "marks" : [
                                        {
                                                "name" : "quiz-1",
                                                "teacher-comment" : "OK",
                                                "mark" : 3
                                        },
                                        {
                                                "name" : "big-test-1",
                                                "teacher-comment" : "OK",
                                                "mark" : 3
                                        }
                                ],
                                "final-mark" : 3
                        }
                ],
                "c" : [
                        {
                                "name" : "Mathematics",
                                "ECTS" : "4"
                        }
                ]
        }