# Introduction
Go router is flutter package that enables to easy navigate between screen, and its better then the navigator . push building in functions.



## How go router works

1.  in order to use go router you should install go router package
```bash
flutter pub add go_router
```

2. then create router file that contains router class as the following
``` 
	class MyRouter{
		final router = GoRouter(
			routes:[
			 // home page 
			 GoRoute(
				 path:'/',
				 name:'homepage',
				 builder: (context,state){
					 return Homepage();
				 }
			 ),
			// about page router
			 GoRoute(
				 path:'/about',
				 name:'about',
				 builder: (context,state){
					 return About();
				 }
			 )
			]
		)
	}
```



3. now connect the router to the main.dart
```flutter
	MaterialApp.router(
	// MyRouter is the class of the router and router is the variable that conatins the routes
		routerConfig:MyRouter().router,
	);
```


4. how to go from one screen to another
```flutter
	// you shoudl button that have click  functionality and put it inside this
	 GoRouter.of(context).go('/');
```

5. Passing data from screen to another
```flutter
// in the router add the following to the path 
GoRoute(

      path: '/about/:name',

      name: 'about',

      builder: (context, state) {
			// this is requried 
        final name = state.pathParameters['name']!;
			// pass the data 
        return About(name: name);

      },

    )

 // pass it 
    final name = 'murad';

  GoRouter.of(context).go('/about/$name');
// and display it 
	// in the screen data are passing to create variable and make it in the state name.
	final name;
const About({super.key , this.name})
Text(this.name)
	  
   

```