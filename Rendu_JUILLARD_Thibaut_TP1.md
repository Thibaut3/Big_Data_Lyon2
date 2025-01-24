JUILLARD Thibaut 
# Rendu


# Premières Requêtes :

## 1)
RQT :
``` js
db.grades.findOne()
```
Nb retourné : 1

Sortie :
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c34e'),
  student_id: 0,
  class_id: 2,
  scores: [
    {
      type: 'exam',
      score: 57.92947112575566
    },
    {
      type: 'quiz',
      score: 21.24542588206755
    },
    {
      type: 'homework',
      score: 68.1956781058743
    },
    {
      type: 'homework',
      score: 67.95019716560351
    },
    {
      type: 'homework',
      score: 18.81037253352722
    }
  ]
}
```

RQT : 
``` js
db.zips.findOne()
```
Nb retourné : 1

Sortie : 
``` js
{
  _id: '01001',
  city: 'AGAWAM',
  loc: [
    -72.622739,
    42.070206
  ],
  pop: 15338,
  state: 'MA'
}
```

## 2)
RQT :
``` js
db.grades.find({})
```
``` js
db.grades.find({}).count()
```
Nb retourné : 280

Sortie : 
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c34e'),
  student_id: 0,
  class_id: 2,
  scores: [
    {
      type: 'exam',
      score: 57.92947112575566
    },
    {
      type: 'quiz',
      score: 21.24542588206755
    },
    {
      type: 'homework',
      score: 68.1956781058743
    },
    {
      type: 'homework',
      score: 67.95019716560351
    },
    {
      type: 'homework',
      score: 18.81037253352722
    }
  ]
}
```

RQT : 
``` js
db.zips.find({})
```
``` js
db.zips.find({}).count()
```
Nb retourné : 29353

Sortie : 
``` js
{
  _id: '01001',
  city: 'AGAWAM',
  loc: [
    -72.622739,
    42.070206
  ],
  pop: 15338,
  state: 'MA'
}
```

## 3)
RQT :
``` js
db.grades.countDocuments()
```
ou 
``` js
db.grades.countDocuments({})
```
Sortie : 280

RQT : 
``` js
db.zips.countDocuments()
```
ou
``` js
db.zips.countDocuments({})
```
Sortie : 29353


## 4)
RQT :
``` js
db.grades.find({"class_id":20})
```
```js
db.grades.find({"class_id":20}).count()
```
Nb retourné : 7

Sortie :
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c37a'),
  student_id: 6,
  class_id: 20,
  scores: [
    {
      type: 'exam',
      score: 55.41495979162525
    },
    {
      type: 'quiz',
      score: 80.78090944766167
    },
    {
      type: 'homework',
      score: 5.32775635719569
    }
  ]
}
```

## 5)
RQT :
``` js
db.grades.find({
	"class_id": {
		$lte:20
		}
	})
```
``` js
db.grades.find({
	"class_id": {
		$lte:20
		}
	}).count()
```
Nb retourné : 188

Sortie : 
``` js
  _id: ObjectId('50b59cd75bed76f46522c34e'),
  student_id: 0,
  class_id: 2,
  scores: [
    {
      type: 'exam',
      score: 57.92947112575566
    },
    {
      type: 'quiz',
      score: 21.24542588206755
    },
    {
      type: 'homework',
      score: 68.1956781058743
    },
    {
      type: 'homework',
      score: 67.95019716560351
    },
    {
      type: 'homework',
      score: 18.81037253352722
    }
  ]
}
```

## 6)
RQT :
``` js
db.grades.find({
	$expr: {
		$gte: [
			"$student_id",
			"$class_id"
			]
		}
	})
```
``` js
db.grades.find({
	$expr: {
		$gte: [
			"$student_id",
			"$class_id"
			]
		}
	}).count()
```
Nb retourné : 188

Sortie : 
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c366'),
  student_id: 3,
  class_id: 3,
  scores: [
    {
      type: 'exam',
      score: 86.2587791014086
    },
    {
      type: 'quiz',
      score: 0.7165465872248866
    },
    {
      type: 'homework',
      score: 70.07859698701473
    },
    {
      type: 'homework',
      score: 61.00984159293741
    }
  ]
}
```

## 7)
RQT :
``` js
db.grades.find({
	"class_id": {
		$gte:10,
		$lte:20
		}
	})
```
``` js
db.grades.find({
	$and: [
		{"class_id": {
				$gte:10
				}
		},
		{"class_id": {
				$lte:20
				}
		}
	]
})
```
Nb retourné :

100
100

Sortie :
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c357'),
  student_id: 0,
  class_id: 11,
  scores: [
    {
      type: 'exam',
      score: 58.83297411100884
    },
    {
      type: 'quiz',
      score: 49.66835710930263
    },
    {
      type: 'homework',
      score: 18.05861540807023
    },
    {
      type: 'homework',
      score: 80.04086698967356
    }
  ]
}

{
  _id: ObjectId('50b59cd75bed76f46522c357'),
  student_id: 0,
  class_id: 11,
  scores: [
    {
      type: 'exam',
      score: 58.83297411100884
    },
    {
      type: 'quiz',
      score: 49.66835710930263
    },
    {
      type: 'homework',
      score: 18.05861540807023
    },
    {
      type: 'homework',
      score: 80.04086698967356
    }
  ]
}
```

## 8)
RQT :
``` js
db.grades.find({},{
			ue:"$class_id",
			etu:"$student_id",
			scores:1
})
```
``` js
db.grades.find({},{
			ue:"$class_id",
			etu:"$student_id",
			scores:1
}).count()
```
Nb retourné : 280

Sortie :
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c34e'),
  scores: [
    {
      type: 'exam',
      score: 57.92947112575566
    },
    {
      type: 'quiz',
      score: 21.24542588206755
    },
    {
      type: 'homework',
      score: 68.1956781058743
    },
    {
      type: 'homework',
      score: 67.95019716560351
    },
    {
      type: 'homework',
      score: 18.81037253352722
    }
  ],
  ue: 2,
  etu: 0
}
```

# Aggregation

## 1)
RQT :
``` js
db.grades.aggregate([
	{$project:{
		somme:{
			$sum:["$class_id","$student_id"]
			},
		"class_id":1,
		"student_id":1,
		"scores":1
		}
	}
])
```
``` js
db.grades.aggregate([
	{$project:{
		somme:{
			$sum:["$class_id","$student_id"]
			},
		"class_id":1,
		"student_id":1,
		"scores":1
		}
	},
	{$count : "count"}
])
```
Nb retourné : 280

Sortie : 
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c34e'),
  student_id: 0,
  class_id: 2,
  scores: [
    {
      type: 'exam',
      score: 57.92947112575566
    },
    {
      type: 'quiz',
      score: 21.24542588206755
    },
    {
      type: 'homework',
      score: 68.1956781058743
    },
    {
      type: 'homework',
      score: 67.95019716560351
    },
    {
      type: 'homework',
      score: 18.81037253352722
    }
  ],
  somme: 2
}
```
et
``` js
{
  count: 280
}
```

## 2)
RQT :
``` js
db.zips.aggregate([
	{$match: {
		pop: {$gte: 10000}
		}
	}
])
```
``` js
db.zips.aggregate([
	{$match: {
		pop: {$gte: 10000}
		}
	},
	{$count: "count"}
])
```
Nb retourné : 7634

Sortie : 
``` js
{
  _id: '01001',
  city: 'AGAWAM',
  loc: [
    -72.622739,
    42.070206
  ],
  pop: 15338,
  state: 'MA'
}
```

## 3)
RQT :
``` js
db.grades.aggregate([
	{$sort:{
		class_id:1,
		student_id:1
		}
	}
])
```
``` js
db.grades.aggregate([
	{$sort:{
		class_id:1,
		student_id:1
		}
	},
	{$count : "count"}
])
```
Nb retourné: 280

Sortie:
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c370'),
  student_id: 4,
  class_id: 0,
  scores: [
    {
      type: 'exam',
      score: 67.50593066420024
    },
    {
      type: 'quiz',
      score: 60.43052278095685
    },
    {
      type: 'homework',
      score: 98.634640715799
    },
    {
      type: 'homework',
      score: 6.719346717934882
    },
    {
      type: 'homework',
      score: 43.61408080940507
    },
    {
      type: 'homework',
      score: 92.01607786819618
    }
  ]
}
```

## 4)
RQT :
``` js
db.grades.aggregate([{$unwind: "$scores"}])
```
``` js
db.grades.aggregate([{$unwind: "$scores"},{$count:"count"}])
```
Nb retourné : 1241

Sortie :
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c34e'),
  student_id: 0,
  class_id: 2,
  scores: {
    type: 'exam',
    score: 57.92947112575566
  }
}
```

## 5)
RQT :
``` js
db.zips.aggregate([
	{$group: {
		_id: "$city",
		_pop: {$min: "$pop"}
		}
	}
])
```
``` js
db.zips.aggregate([
	{$group: {
		_id: "$city",
		_pop: {$min: "$pop"}
		}
	},
	{$count : "count"}
])
```
Nb retourné : 16584

Sortie :
``` js
{
  _id: 'SEASIDE HEIGHTS',
  _pop: 4044
}
```

## 6)
RQT :
``` js
db.grades.aggregate([
	{$lookup: {
		from: "zips",
		localField: "student_id",
		foreignField: "pop",
		as : "concate"
		}
	}
])
```
``` js
db.grades.aggregate([
	{$lookup: {
		from: "zips",
		localField: "student_id",
		foreignField: "pop",
		as : "concate"
		}
	},
	{$count: "count"}
])
```
Nb retourné : 280

Sortie :
``` js
{
  _id: ObjectId('50b59cd75bed76f46522c34e'),
  student_id: 0,
  class_id: 2,
  scores: [
    {
      type: 'exam',
      score: 57.92947112575566
    },
    {
      type: 'quiz',
      score: 21.24542588206755
    },
    {
      type: 'homework',
      score: 68.1956781058743
    },
    {
      type: 'homework',
      score: 67.95019716560351
    },
    {
      type: 'homework',
      score: 18.81037253352722
    }
  ],
  concate: [
    {
      _id: '02163',
      city: 'CAMBRIDGE',
      loc: [
        -71.141879,
        42.364005
      ],
      pop: 0,
      state: 'MA'
    },
    {
      _id: '04013',
      city: 'BUSTINS ISLAND',
      loc: [
        -70.042247,
        43.79602
      ],
      pop: 0,
      state: 'ME'
    },
…
    {
      _id: '99770',
      city: 'SELAWIK',
      loc: [
        -158.534287,
        65.713537
      ],
      pop: 0,
      state: 'AK'
    },
    {
      _id: '99773',
      city: 'SHUNGNAK',
      loc: [
        -157.613496,
        66.958141
      ],
      pop: 0,
      state: 'AK'
    }
  ]
}
```

# Pipelines 

## 1)
RQT :
``` js
db.grades.aggregate([
    { $unwind: "$scores" },
    { $group: {
        _id: "$scores.type",
        count: { $sum: 1 }
    }}
])
```
``` js
db.grades.aggregate([
    { $unwind: "$scores" },
    { $group: {
        _id: "$scores.type",
        count: { $sum: 1 }
    }},
    { $count: "count" }
])
//Résu
```
Nb retourné : 3

Sortie :
``` js
{
  _id: 'homework',
  count: 681
},
{
  _id: 'quiz',
  count: 280
},
{
  _id: 'exam',
  count: 280
}
```


## 2)
RQT :
``` json
db.grades.aggregate([
    { $unwind: "$scores" },
    { $match: { "scores.type": "exam" } },
    { $group: {
        _id: "$class_id",
        best_exam_score: { $max: "$scores.score" }
    }}
])
```
``` js
db.grades.aggregate([
    { $unwind: "$scores" },
    { $match: { "scores.type": "exam" } },
    { $group: {
        _id: "$class_id",
        best_exam_score: { $max: "$scores.score" }
    }},
    { $count: "count" }
])
```
Nb retourné : 31
Sortie :
``` js
[
    {
    _id: 25,
    best_exam_score: 88.80822542748272
    },
    {
    _id: 11,
    best_exam_score: 99.40117530792308
    },
    .,
    .,
    .,
    {
    _id: 6,
    best_exam_score: 99.49380951735357
    },
]
```


## 3)
RQT :
```
db.zips.aggregate([
    { $group: {
        _id: "$city",
        total_population: { $sum: "$pop" }
    }},
    { $sort: { total_population: -1 } },
    { $limit: 10 }
])
```
``` js
db.zips.aggregate([
    { $group: {
        _id: "$city",
        total_population: { $sum: "$pop" }
    }},
    { $sort: { total_population: -1 } },
    { $count: "count" }
])
```
Nb retourné : 16584
Sortie : 
``` js
[
    {
        _id: 'CHICAGO',
        total_population: 2452177
    },
    {
        _id: 'BROOKLYN',
        total_population: 2341387
    },
    {
        _id: 'HOUSTON',
        total_population: 2123053
    },
    .,
    .,
    .,
    {
        _id: 'DETROIT',
        total_population: 967468
    }

]
```


## 4)
RQT :
``` js
db.zips.aggregate([
    { $group: {
        _id: "$state",
        average_city_population: { $avg: "$pop" }
    }},
])
```
``` js
db.zips.aggregate([
    { $group: {
        _id: "$state",
        average_city_population: { $avg: "$pop" }
    }},
    { $count: "count" }
])
```
Nb retourné : 51
Sortie :
``` js
[
    {
    _id: 'MS',
    average_city_population: 7088.749311294766
    },
    {
    _id: 'DC',
    average_city_population: 25287.5
    },
    {
    _id: 'UT',
    average_city_population: 8404.146341463415
    }
    .,
    .,
    .,
    {
    _id: 'WV',
    average_city_population: 2733.454268292683
    }
]
```


## 5)
RQT :
``` js
db.grades.aggregate([
    { $unwind: "$scores" },
    { $match: { "scores.type": "exam", "scores.score": { $gt: 50 } } },
    { $group: {
        _id: "$class_id",
        students_with_high_scores: { $push: "$student_id" }
    }}
```
``` js
db.grades.aggregate([
    { $unwind: "$scores" },
    { $match: { "scores.type": "exam", "scores.score": { $gt: 50 } } },
    { $group: {
        _id: "$class_id",
        students_with_high_scores: { $push: "$student_id" }
    }},
    { $count: "total_states" }
])
```
Nb retourné : 31

Sortie :
``` js
[
    {
    _id: 25,
    students_with_high_scores: [
        3,
        34,
        37,
        45
    ]
    },
    {
    _id: 11,
    students_with_high_scores: [
        0,
        3,
        8,
        12,
        14,
        23,
        44
    ]
    },
    {
    _id: 3,
    students_with_high_scores: [
        3,
        9,
        20,
        30,
        37
    ]
    },
    .,
    .,
    .,
    {
    _id: 6,
    students_with_high_scores: [
        0,
        14,
        29,
        30,
        36,
        45
    ]
    }
]
```


## 6)
RQT :
``` js
db.grades.aggregate([
    { $unwind: "$scores" },
    { $group: {
        _id: {
            student_id: "$student_id",
            class_id: "$class_id",
            type: "$scores.type"
        },
        average_score_per_type: { $avg: "$scores.score" }
    }},
    { $group: {
        _id: {
            student_id: "$_id.student_id",
            class_id: "$_id.class_id"
        },
        overall_average: { $avg: "$average_score_per_type" }
    }},
    { $project: {
        _id: 0,
        student_id: "$_id.student_id",
        class_id: "$_id.class_id",
        general_score: "$overall_average"
    }}
])
```
Nb retourné : 280
Sortie :
``` js
[
    {
    student_id: 29,
    class_id: 11,
    general_score: 61.86708165994667
    },
    {
    student_id: 38,
    class_id: 17,
    general_score: 41.39964272948872
    },
    {
    student_id: 8,
    class_id: 29,
    general_score: 53.41590432424875
    },
    .,
    .,
    .,
    {
    student_id: 9,
    class_id: 8,
    general_score: 25.805171079654958
    }
]
```


## 7)
RQT :
``` js
db.grades.aggregate([
    { $unwind: "$scores" },
    { $group: {
        _id: {
            class_id: "$class_id",
            type: "$scores.type"
        },
        average_score: { $avg: "$scores.score" }
    }},
    { $group: {
        _id: "$_id.class_id",
        averages: { $push: { type: "$_id.type", avg: "$average_score" } },
        best_average: { $max: "$average_score" }
    }},
    { $project: {
        _id: 0,
        class_id: "$_id",
        best_type: {
            $arrayElemAt: [
                "$averages",
                { $indexOfArray: ["$averages.avg", "$best_average"] }
            ]
        }
    }}
])
```
Nb retourné : 31

Sortie :
``` js
[
    {
    class_id: 25,
    best_type: {
        type: 'quiz',
        avg: 48.595580262242
    }
    },
    {
    class_id: 11,
    best_type: {
        type: 'quiz',
        avg: 66.78875217934441
    }
    },
    {
    class_id: 3,
    best_type: {
        type: 'homework',
        avg: 52.578328231929646
    }
    },
    .,
    .,
    .,
    {
    class_id: 6,
    best_type: {
        type: 'exam',
        avg: 59.62558171984689
    }
]
```



