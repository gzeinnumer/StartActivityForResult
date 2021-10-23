# StartActivityForResult
 
- MainActivity.java
```java
Intent intent = new Intent(getApplicationContext(), SecondActivity.class);
someActivityResultLauncher.launch(intent);
```
```java
ActivityResultLauncher<Intent> someActivityResultLauncher = registerForActivityResult(
        new ActivityResultContracts.StartActivityForResult(),
        new ActivityResultCallback<ActivityResult>() {
            @Override
            public void onActivityResult(ActivityResult result) {
                if (result.getResultCode() == 2) {
                    // There are no request codes
                    Intent data = result.getData();
                    doSomeOperations(data);
                }
            }
        });

private void doSomeOperations(Intent data) {
    String message = data.getStringExtra("MESSAGE");
    textView1.setText(message);
}
```

- SecondActivity.java
```java
String message = editText1.getText().toString();
Intent intent = new Intent();
intent.putExtra("MESSAGE", message);
setResult(Activity.RESULT_OK, intent);
finish();//finishing activity
```

---

```
Copyright 2021 M. Fadli Zein
```