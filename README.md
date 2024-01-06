```php
// ------------------------
 DB::table('students')->get();
$results= DB::table('results')->get();
$publish= $students->merge($results);
print_r($publish);
exit();
// ------------------------

 DB::select('select * from students');
 DB::table('students')->get();
 DB::table('students')->where('id',3)->get();
 DB::table('students')->where('name','admin')->get();
 DB::table('students')->where('name','admin')->where('age','>',20)->get();
 DB::table('students')->where([
    ['name','=','dhaka'],
    ['age','>',20]
 ])->get();
 DB::table('users')->whereBetween('id', [1, 100])->get();
 DB::table('students')->where('name','admin')->orWhere('age','>',20)->get();
 DB::table('students')->whereBetween('id',[2,4])->get();
 DB::table('students')->whereNotBetween('id',[1,2])->get();
 DB::table('students')->whereIn('id',[1,2,3])->get();
 DB::table('students')->where('name', 'admina')->orWhere(
    function ($query) {
        $query->where('name', 'aaa2')
        ->OrWhere('name','aaa3');
    }
)->get();
 DB::table('students')->whereDate('created_at', '2023-02-01')->get();
 DB::table('students')->whereMonth('created_at', '1')->get();
 DB::table('students')->whereDay('created_at', '1')->get();
 DB::table('students')->whereYear('created_at', '2023')->get();
 DB::table('students')->whereYear('created_at', '2023')->whereMonth('created_at', '2')->get();
 DB::table('students')->whereColumn('updated_at','<','created_at')->get();
 DB::table('students')->where('id','3')->get();
 DB::table('students')->where('id','3')->get();
 DB::table('students')->find(3);
 DB::table('students')->where('id',3)->value('email');
 DB::table('students')->select('id','name','email')->get();

way rwo
 DB::table('students')->select('id');
$result= $students->addselect('email','phone')->get();
print_r($result);
exit();
way two

dd($students);
 DB::table('students')->get();
 DB::table('students')->orderBy('name','desc')->get();
 DB::table('students')->select('email')->groupBy('email')->get();
 DB::table('students')->offset(1)->limit(1)->get();
union
$student= DB::table('students')->where('id',4);
DB::table('students')->where('name','admin')->union($student)->get();
union
DB::table('students')->where('id','>',6)->count();
DB::table('students')->max('id');
DB::table('students')->min('id');
DB::table('students')->avg('id');
DB::table('students')->sum('id');

 DB::table('students')->orderBy('id')->chunk(5, function ($users) {
    foreach ($users as $value) {
        echo $value->name;
    }
});
exit();


if (DB::table('students')->where('name', 'admin')->exists()) {
    echo 'exist';
}

DB::table('students')->rightJoin('results','students.id','=','results.students_id')->get();
DB::table('students')->crossJoin('results')->get();

DB::table('districts')->righJoin('cities','districts.id','=','cities.district_id')->get();
[id] => 718
[district_name] => Dhaka
[created_at] =>
[updated_at] =>
[city_name] => Ashulia
[district_id] => 1
// --------------------------------------------------------------------
DB::table('districts')->rightJoin('cities','districts.id','=','cities.district_id')->get();
[id] => 1
[district_name] => Dhaka
[created_at] =>
[updated_at] =>
[city_name] => Adabor
[district_id] => 1
```

```php
// ----------
$post = Post::doesntHave('comments')->get();
dd($post);
dd($post[3]->name);
// -----------


// withCount
$post = Post::withCount(['comments'])->get();
dd($post);
// withCount

// morphedByMany
$post = Post::find(2);
$tag = Tag::find(3);
dd($tag->videos);
$tag = Tag::find(3);
dd($tag->posts);
// morphedByMany


// morphOne
$post = Post::find(1);
$video = Video::find(1);
$comment = Comment::find(1);
dd($post->commentmodel);
dd($comment->commentable);
// morphOne


// ------------------------
 DB::table('students')->get();
$results= DB::table('results')->get();
$publish= $students->merge($results);
print_r($publish);
exit();
// ------------------------

 DB::select('select * from students');
 DB::table('students')->get();
 DB::table('students')->where('id',3)->get();
 DB::table('students')->where('name','admin')->get();
 DB::table('students')->whereBetween('id',[2,4])->get();
 DB::table('students')->whereNotBetween('id',[1,2])->get();
 DB::table('students')->whereIn('id',[1,2,3])->get();
 DB::table('students')->where('name', 'admina')->orWhere(
    function ($query) {
        $query->where('name', 'aaa2')
        ->OrWhere('name','aaa3');
    }
)->get();
 DB::table('students')->whereDate('created_at', '2023-02-01')->get();
 DB::table('students')->whereMonth('created_at', '1')->get();
 DB::table('students')->whereDay('created_at', '1')->get();
 DB::table('students')->whereYear('created_at', '2023')->get();
 DB::table('students')->whereYear('created_at', '2023')->whereMonth('created_at', '2')->get();
 DB::table('students')->whereColumn('updated_at','<','created_at')->get();
 DB::table('students')->where('id','3')->get();
 DB::table('students')->where('id','3')->get();
 DB::table('students')->find(3);
 DB::table('students')->where('id',3)->value('email');
 DB::table('students')->select('id','name','email')->get();

// way rwo
 DB::table('students')->select('id');
$result= $students->addselect('email','phone')->get();
print_r($result);
exit();
// way two

dd($students);
 DB::table('students')->get();
 DB::table('students')->orderBy('name','desc')->get();
 DB::table('students')->select('email')->groupBy('email')->get();
 DB::table('students')->offset(1)->limit(1)->get();
// union
$student= DB::table('students')->where('id',4);
DB::table('students')->where('name','admin')->union($student)->get();

//2
$letcureres =DB::table('lecturers')->select('name', 'email'); //condion is both table column name & data type
DB::table('students')->union($letcureres)->select('name', 'email')->get();//condion is both table column name & data type

//3
$letcureres =DB::table('lecturers'); //condion is both table column name & data type
DB::table('students')->union($letcureres)->get();//condion is both table column name & data type

// union
DB::table('students')->where('id','>',6)->count();
DB::table('students')->max('id');
DB::table('students')->min('id');
DB::table('students')->avg('id');
DB::table('students')->sum('id');

 DB::table('students')->orderBy('id')->chunk(5, function ($users) {
    foreach ($users as $value) {
        echo $value->name;
    }
});
exit();


if (DB::table('students')->where('name', 'admin')->exists()) {
    echo 'exist';
}

DB::table('students')->rightJoin('results','students.id','=','results.students_id')->get();
DB::table('students')->crossJoin('results')->get();

DB::table('districts')->righJoin('cities','districts.id','=','cities.district_id')->get();
// [id] => 718
// [district_name] => Dhaka
// [created_at] =>
// [updated_at] =>
// [city_name] => Ashulia
// [district_id] => 1
// --------------------------------------------------------------------
DB::table('districts')->rightJoin('cities','districts.id','=','cities.district_id')->get();
// [id] => 1
// [district_name] => Dhaka
// [created_at] =>
// [updated_at] =>
// [city_name] => Adabor
// [district_id] => 1
return view('welcome', ['students' => $students]);
```

- insert data

```php
DB::table('users')->insert([
    'name' => "user",
    'email' => 'kayla@example.com',
    'created_at' => now(),
    'updated_at' => now(),
]);

DB::table('users')->upsert(
[
    [
    'name' => "user",
    'email' => 'kayla@example.com',
    'created_at' => now(),
    'updated_at' => now(),
    ],
    ['email']
]
);

```

```php
public function index(){
    //hasOneThrough relation mechanic Owner Car
    $mechanic = Mechanic::with('carowner')->get();
    dd($mechanic);
    // hasOneThrough relation mechanic Owner Car

    // ---------------------------------------------
    // belongsTo resultToStudent model one to one reverse
    $result= Result::get();
    dd($result[1]->student);
    // belongsTo student model one to one reverse


    // hasone studentToResult model one to one
    $student= Student::with('result')->get();
    $student= Student::get();
    dd($student->result);
    dd($student);
    dd($student[0]->result->roll);
    // hasone studentToResult model one to one


    // hasmany studentToResult model one to many
    $student= Student::with('resulthasmany')->get();
    $student= Student::get();
    dd($student->result);
    dd($student);
    dd($student[0]->result->roll);
    // hasmany studentToResult model one to many

    $student= Student::get();
    $student= Student::with('result')->get();
    dd($student->result->phone);
    dd($student[1]->result);
    dd($student->result);

    $student= Student::create([
        'name'=>'author',
        'email'=>'author@gmail.com',
    ]);

    $student->name= 'addy';
    echo $student->isDirty();

    $student= Student::addSelect(['student_name'=>Student::select('name')->whereColumn('student_id','student.id')
]);

    $student= User::all();
    $student= User::get();
    $student= User::where('name','admin')->get();

    $student= User::chunk(3, function($students){
        foreach($students as $value){
            echo $value;
        }
        echo "<br>";
    });

    foreach(User::where('id','<','10')->cursor() as $student){
        echo $student;
    }

    $student= User::find(4);
    $student= User::where('name','user')->first(); // id 2 user, id 6 user = print id 2
    $student= User::firstWhere('name','user2');
    return view('welcome');
}
function store(Request $request){
    $id=$request->id;
    $data = array(
        'name' => $request->name,
        'email' => $request->email,
        'phone' => $request->phone,
    );
    User::upsert($data, ['id'], ['phone']);
}
function edit(Request $request){
    $id=$request->id;
    $student= Student::edit($id);
    $student= Student::find($id);
    $student= Student::findOrFail($id);
    $student= Student::firstOrCreate([
        'name'=>'admin'
    ]);

    $student= Student::firstOrCreate([
        'name'=>'admin'
    ],['phone'=>'1234','email'=>'aa@gmail.com']);

    $student= Student::where('name','anmol')->count();

    $student= Student::max('id');
    $student= Student::sum('id');


    $student= Student::where('id',$id)->firstOrFail();\

}
function update(Request $request){
    $id=$request->id;
    $data = array(
        'name' => $request->name,
        'email' => $request->email,
        'phone' => $request->phone,
    );
    User::where('id',$id)->update($data);

    $id=$request->id;
    $student= User::find($id);
    $student->name= $request->name;
    $student->email= $request->email;
    $student->phone= $request->phone;
    $student->save();
}
function delete(Request $request){
    $id=$request->id;
    $student= Student::find($id)->delete();

    $id=$request->id;
    $student= Student::destroy($id);
    $student= Student::destroy(2,5,6);
}
```

### Database: Seeding

- laravel/database/seeders/DatabaseSeeder.php
- Writing Seeders

* seed all

```bash
php artisan db:seed
```

- seed only UserSeeder table | single table

```bash
php artisan make:seeder UserSeeder
```

- Both code snippets insert a new user into the users table in Laravel, but they use different approaches and have different use cases

```php
use App\Models\User;
use Illuminate\Database\Seeder;
use Illuminate\Support\Facades\DB;
use Illuminate\Support\Facades\Hash;
use Illuminate\Support\Str;
class DatabaseSeeder extends Seeder
{
     public function run(): void
     {
        User::factory()->create([
             'name' => 'app Service Provider',
             'email' => 'appServiceProvider@gmail.com',
             'password' => bcrypt('123456'),
         ]);
        //  --------------------------------------
         DB::table('users')->insert([
            'name' => Str::random(10),
            'email' => Str::random(10).'@gmail.com',
            'password' => Hash::make('password'),
        ]);
        //  --------------------------------------
        for ($i = 0; $i < 100; $i++) {
        DB::table('users')->insert([
        'name' => Str::random(10),
        'email' => Str::random(10) . '@gmail.com',
        'password' => Hash::make('password'),
        ]);
        };
        // ---------Or------------------------
        User::factory(){
        ->count(50)
        // ->hasPosts(1)
        ->create();
        }// its related factories | laravel/database/factories/UserFactory.php https://fakerphp.github.io/

        // ---------Or------------------------
        User::factory()->count(50)->create();

     }
}
```

<!-- -------------------Or------------ -->

```bash
      $stds = collect([
         [
             'name' => 'app Service ',
             'email' => 'appSerieProvider@gmail.com',
             'password' => bcrypt('123456'),
         ],
         [
             'name' => 'app Service Provider',
             'email' => 'appServiceProvder@gmail.com',
             'password' => bcrypt('123456'),
         ],
         [
             'name' => 'app ',
             'email' => 'apServiceProvder@gmail.com',
             'password' => bcrypt('123456'),
         ],
     ]);
     $stds->each(function ($std) {
         User::insert($std);
     });
```

<!-- --------------------------------------------- -->

```bash
 protected static ?string $password;
   public function run(): void
   {
    for($i=0; $i<10; $i++){
        User::create([
            'name' => fake()->name(),
            'email' => fake()->unique()->freeEmail(),
            'email_verified_at' => now(),
            'password' => static::$password ??= Hash::make('password'),
            'remember_token' => Str::random(10),
        ]);
    }
   }
```

<!-- ---------------------------------------------------- -->

```php
   public function run(): void
   {
    /*
      $json =File::get(path:'database/user.json');
      $stdCollect= collect(json_decode($json));
      $stdCollect->each(function($std){
         User::create([
            'name'=> $std->name,
            'email'=> $std->email,
         ]);
      });
      */

      $json = File::get(database_path('user.json')); // Use database_path to get the correct path
      $usersData = json_decode($json);

      collect($usersData)->each(function ($userData) {
          User::create([
              'name' => $userData->name,
              'email' => $userData->email,
              'password' => $userData->password ?? Hash::make('password'),
          ]);
      });

   }
```

<!-- ------------------------------------------------------- -->

- This command is a combination of two steps:

* migrating the database and running seeders.

```bash
php artisan migrate --seed
```

- helpfull command

```bash
php artisan make:factory StudentFactory
php artisan make:factory StudentFactory --model=Student (factory & model)
php artisan make:model -f --model=Student (factory & model)

php artisan db:seed
php artisan db:seed --class=StudentSeeder
php artisan migrate:fresh --seed (migration & seeding)
```

- on production topup command does not run allow only forcefuly

```bash
php artisan db:seed --force
php artisan db:seed --class=StudentSeeder --force
```

- laravel/database/factories/ProductSeeder.php call to DatabaseSeed

```php
class ProductSeeder extends Seeder
{
    public function run(): void
    {
        $this->call([
            DatabaseSeeder::class,
        ]);
    }
}
```

```bash
php artisan db:seed --class=ProductSeeder
```
