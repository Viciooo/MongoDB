# Add documents

        use pw;
        show collections

### Paste student to mongoshell

        student = {
        "firstname": "John",
        "lastname": "Doe",
        "email": "JohnDoe@email.com",
        "gender" : "m",
        "favourite_subjects": ["Physics","Math","IT"],
        "student_status_active" : true,
        "subjects" : {
            "Physics": {
                "mark": 2,
                "teachers_comment": "smart boy"
            },
            "Chemistry": {
                "mark": 5,
                "teachers_comment": "ok"
            },
            "Biology": {
                "mark": 1,
            },
            "Ecology": {
                "mark": 4,
                "teachers_comment": "meh"
            },
            "Food Science":{
                "mark": 5,
            }
        },
    }

        db.student.insert(student)

    student1 = {
        "firstname": "Mike",
        "lastname": "Tv",
        "email": "MikeTv@email.com",
        "gender" : "m",
        "favourite_subjects": ["English","Math"],
        "student_status_active" : false,
        "subjects" : {
            "Math": {
                "mark": 1,
                "teachers_comment": "smart boy"
            },
            "Biology": {
                "mark": 3,
            },
            "PE": {
                "mark": 5,
                "teachers_comment": "Superb"
            },
        },
    }

    db.student.insert(student1)

        student3 = {
        "firstname": "Katy",
        "lastname": "Boo",
        "email": "Kboo@email.com",
        "gender" : "f",
        "favourite_subjects": ["English","Math"],
        "student_status_active" : true,
        "subjects" : {
            "Math": {
                "mark": 5,
                "teachers_comment": "xoxo"
            },
            "Arts": {
                "mark": 5,
            },
            "PE": {
                "mark": 5,
                "teachers_comment": "cute looking"
            },
        },
    }

    db.student.insert(student3)


    db.student.find().pretty()

## We can add many documents:
    
### paste:

        students = [
        {
            "firstname": "Katy",
            "lastname": "Boo",
            "email": "Kboo@email.com",
            "gender" : "f",
            "favourite_subjects": ["English","Math"],
            "student_status_active" : true,
            "subjects" : {
                "Math": {
                    "mark": 5,
                    "teachers_comment": "xoxo"
                },
                "Arts": {
                    "mark": 5,
                },
                "PE": {
                    "mark": 5,
                    "teachers_comment": "cute looking"
                },
            },
        },
        {
            "firstname": "Katy",
            "lastname": "Boo",
            "email": "Kboo@email.com",
            "gender" : "f",
            "favourite_subjects": ["English","Math"],
            "student_status_active" : true,
            "subjects" : {
                "Math": {
                    "mark": 5,
                    "teachers_comment": "xoxo"
                },
                "Arts": {
                    "mark": 5,
                },
                "PE": {
                    "mark": 5,
                    "teachers_comment": "cute looking"
                },
            },
        },{
            "firstname": "Katy",
            "lastname": "Boo",
            "email": "Kboo@email.com",
            "gender" : "f",
            "favourite_subjects": ["English","Math"],
            "student_status_active" : true,
            "subjects" : {
                "Math": {
                    "mark": 5,
                    "teachers_comment": "xoxo"
                },
                "Arts": {
                    "mark": 5,
                },
                "PE": {
                    "mark": 5,
                    "teachers_comment": "cute looking"
                },
            },
        },
        {
            "firstname": "Mike",
            "lastname": "Tv",
            "email": "MikeTv@email.com",
            "gender" : "m",
            "favourite_subjects": ["English","Math"],
            "student_status_active" : false,
            "subjects" : {
                "Math": {
                    "mark": 1,
                    "teachers_comment": "smart boy"
                },
                "Biology": {
                    "mark": 3,
                },
                "PE": {
                    "mark": 5,
                    "teachers_comment": "Superb"
                },
            },
        },{
            "firstname": "John",
            "lastname": "Doe",
            "email": "JohnDoe@email.com",
            "gender" : "m",
            "favourite_subjects": ["Physics","Math","IT"],
            "student_status_active" : true,
            "subjects" : {
                "Physics": {
                    "mark": 2,
                    "teachers_comment": "smart boy"
                },
                "Chemistry": {
                    "mark": 5,
                    "teachers_comment": "ok"
                },
                "Biology": {
                    "mark": 1,
                },
                "Ecology": {
                    "mark": 4,
                    "teachers_comment": "meh"
                },
                "Food Science":{
                    "mark": 5,
                }
            },
        }
    ]

### and then:

        db.student.insertMany(students)

# Finding specific documents

        db.student.find({firstname: 'John'}).pretty()

`RESULT:`

        {
                "_id" : ObjectId("624b2feb429f33ce1c1485ce"),
                "firstname" : "John",
                "lastname" : "Doe",
                "email" : "JohnDoe@email.com",
                "gender" : "m",
                "favourite_subjects" : [
                        "Physics",
                        "Math",
                        "IT"
                ],
                "student_status_active" : true,
                "subjects" : {
                        "Physics" : {
                                "mark" : 2,
                                "teachers_comment" : "smart boy"
                        },
                        "Chemistry" : {
                                "mark" : 5,
                                "teachers_comment" : "ok"
                        },
                        "Biology" : {
                                "mark" : 1
                        },
                        "Ecology" : {
                                "mark" : 4,
                                "teachers_comment" : "meh"
                        },
                        "Food Science" : {
                                "mark" : 5
                        }
                }
        }
        {
                "_id" : ObjectId("624b32cf429f33ce1c1485d5"),
                "firstname" : "John",
                "lastname" : "Doe",
                "email" : "JohnDoe@email.com",
                "gender" : "m",
                "favourite_subjects" : [
                        "Physics",
                        "Math",
                        "IT"
                ],
                "student_status_active" : true,
                "subjects" : {
                        "Physics" : {
                                "mark" : 2,
                                "teachers_comment" : "smart boy"
                        },
                        "Chemistry" : {
                                "mark" : 5,
                                "teachers_comment" : "ok"
                        },
                        "Biology" : {
                                "mark" : 1
                        },
                        "Ecology" : {
                                "mark" : 4,
                                "teachers_comment" : "meh"
                        },
                        "Food Science" : {
                                "mark" : 5
                        }
                }
        }


## We use dot notation to find nested properties:

        db.student.find({'subjects.Math.mark': 5}).pretty()

`RESULT:`

        {
                "_id" : ObjectId("624b318e429f33ce1c1485d0"),
                "firstname" : "Katy",
                "lastname" : "Boo",
                "email" : "Kboo@email.com",
                "gender" : "f",
                "favourite_subjects" : [
                        "English",
                        "Math"
                ],
                "student_status_active" : true,
                "subjects" : {
                        "Math" : {
                                "mark" : 5,
                                "teachers_comment" : "xoxo"
                        },
                        "Arts" : {
                                "mark" : 5
                        },
                        "PE" : {
                                "mark" : 5,
                                "teachers_comment" : "cute looking"
                        }
                }
        }
        {
                "_id" : ObjectId("624b32cf429f33ce1c1485d1"),
                "firstname" : "Katy",
                "lastname" : "Boo",
                "email" : "Kboo@email.com",
                "gender" : "f",
                "favourite_subjects" : [
                        "English",
                        "Math"
                ],
                "student_status_active" : true,
                "subjects" : {
                        "Math" : {
                                "mark" : 5,
                                "teachers_comment" : "xoxo"
                        },
                        "Arts" : {
                                "mark" : 5
                        },
                        "PE" : {
                                "mark" : 5,
                                "teachers_comment" : "cute looking"
                        }
                }
        }
        {
                "_id" : ObjectId("624b32cf429f33ce1c1485d2"),
                "firstname" : "Katy",
                "lastname" : "Boo",
                "email" : "Kboo@email.com",
                "gender" : "f",
                "favourite_subjects" : [
                        "English",
                        "Math"
                ],
                "student_status_active" : true,
                "subjects" : {
                        "Math" : {
                                "mark" : 5,
                                "teachers_comment" : "xoxo"
                        },
                        "Arts" : {
                                "mark" : 5
                        },
                        "PE" : {
                                "mark" : 5,
                                "teachers_comment" : "cute looking"
                        }
                }
        }
        {
                "_id" : ObjectId("624b32cf429f33ce1c1485d3"),
                "firstname" : "Katy",
                "lastname" : "Boo",
                "email" : "Kboo@email.com",
                "gender" : "f",
                "favourite_subjects" : [
                        "English",
                        "Math"
                ],
                "student_status_active" : true,
                "subjects" : {
                        "Math" : {
                                "mark" : 5,
                                "teachers_comment" : "xoxo"
                        },
                        "Arts" : {
                                "mark" : 5
                        },
                        "PE" : {
                                "mark" : 5,
                                "teachers_comment" : "cute looking"
                        }
                }
        }
    
# Deleting

        db.student.deleteOne({_id : ObjectId("624b32cf429f33ce1c1485d2")})

`RESULT:`

        { "acknowledged" : true, "deletedCount" : 1 }

# Modifing

        db.student.update({_id : ObjectId("624b32cf429f33ce1c1485d5")},{$set:{firstname: 'Maria'}})

`RESULT:`

        WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })        