يستعمل الأندرويد للتعرف على الكلام إلى مجموعة فئات من ال- API مجمعة في حزمة  android.speech وبالتحديد يستعمل  الطبقة android.speech.RecognizerIntent . نقوم أساسا إلى إصدار أمر نوايا ( android.speech.RecognizerIntent ) الذي يقوم بأظهار مربع الحوار و البدء في التعرف على الكلام المدخل . تقوم هذه الفئة إلى تحويل الكلام إلى نص وإرسال النتيجة إلى النشاط الأصلي المصدر لأمر النية  . عند استدعائنا لأمر  android.speech.RecognizerIntent النية ، يجب علينا أن نستخدم startActivityForResult () كما يجب علينا أن نستمع كذلك للنتيجة لتلقي النص.
لاحظ كيف في التعليمات البرمجية أعلاه نقوم بإصدار أمرالنية android.speech.RecognizerIntent و كذلك نضيف معلمة إضافية باستخدام الأسلوب. PutExtra ( ) . عند استدعاء RecognizerIntent ، يجب علينا توفير RecognizerIntent.EXTRA_LANGUAGE_MODE إضافية. نحن هنا نحدد قيمة اللغة ل EN-US.

و كما هو الحال عند إصدار أمر نية  RecognizerIntent عبر startActivityForResult ( ) فيجب  تلقي نتيجة النشاط بإستعمال  onActivityResult (الباحث requestCode ، وكثافة العمليات resultCode ، وبيانات النوايا ) لمعالجة النتيجة.
RecognizerIntent سيقوم  بتحويل الكلام إلى نص وإرساله مرة أخرى كنتيجة في شكل  ArraList مع RecognizerIntent.EXTRA_RESULTS الرئيسية.
عموما يجب  أن ترتب هذه القائمة في ترتيب تنازلي من الكلام المتعرف عليه  وتكون متوفرة فقط إذا تم إرجاع RESULT_OK في نتيجة النشاط. 
شيء واحد الجدير بالذكر هنا هو كيفية التعامل مع أجهزة الأندرويد التي  لا تدعم ترجمة الكلام إلى نص . في مثل هذه الحالة سوف يلقى إستثناء ActivityNotFoundException عند محاولة بدء النشاط

