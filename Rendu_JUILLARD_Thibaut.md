JUILLARD Thibaut 
# Rendu


# Premières Requêtes :

1)
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

2)
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

3)
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


4)
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

6)
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

8)
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

10)
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

8)
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

1)
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

2)
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

4)
RQT :
db.grades.aggregate([{$unwind: "$scores"}])
db.grades.aggregate([{$unwind: "$scores"},{$count:"count"}])
Nb retourné : 1241
Sortie :
{
  _id: ObjectId('50b59cd75bed76f46522c34e'),
  student_id: 0,
  class_id: 2,
  scores: {
    type: 'exam',
    score: 57.92947112575566
  }
}


5)
RQT :
db.zips.aggregate([{$group: {_id: "$city", _pop: {$min: "$pop"}}}])
db.zips.aggregate([{$group: {_id: "$city", _pop: {$min: "$pop"}}},{$count : "count"}])
Nb retourné : 16584
Sortie :
{
  _id: 'SEASIDE HEIGHTS',
  _pop: 4044
}


6)
RQT : 
db.grades.aggregate([{$lookup: {from: "zips", localField: "student_id", foreignField: "pop", as : "concate"}}])
db.grades.aggregate([{$lookup: {from: "zips", localField: "student_id", foreignField: "pop", as : "concate"}},{$count: "count"}])
Nb retourné : 280
Sortie :
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


# Pipelines 




