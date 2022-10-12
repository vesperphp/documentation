# Cross Site Request Forgery

Vesper-PHP has built in csrf that is easy to use. When a POST request is executed the value is automatically checked and after that a reset is ran.
To use csrf in your form just add {{ _csrf; }} to your html form. This will add a hidden input with the data in it. And after that you are done.

The comparison is handled in the Model class so it is active in all well formed models with controllers. If you need it somewhere else, just use this:

```
public function csrf(){

    if(!empty(Request::post()) && !Cross::path()){

        die('Failsafe triggered on model.');

    } 
}
```