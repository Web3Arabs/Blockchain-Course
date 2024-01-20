---
title: ما هي الأجهزة الافتراضية لإيثريوم (EVM)؟
index: 11
contract: false
---

# ما هي الأجهزة الافتراضية لإيثريوم (EVM)؟

الأجهزة الافتراضية (VM) هو جهاز كمبيوتر يعمل على شبكة blockchain ويسمح للعقود الذكية من مصادر متعددة بالتفاعل مع بعضها البعض. ,العقد الذكي هو ببساطة اتفاقية، يتم التعبير عنها في أكواد برمجية، ويتم تنفيذها على شبكة blockchain، واللغة التي يتم إستخدمها خاصة بشبكة ال blockchain. لتشغيل العقود الذكية على شبكات blockchain مختلفة، نحتاج إلى أجهزة افتراضية للسماح للعقود الذكية المكتوبة بلغة معينة بأن تعمل في شبكة blockchain آخر مما يوفر الوقت والتكاليف مقارنة بإعادة كتابة واختبار العقود الذكية الجديدة أو حتى مطالبة المطورين بتعلم لغة برمجة جديدة.

توجد شبكة Ethereum فقط لغرض الحفاظ على التشغيل الفردي والمستمر وغير المنقطع وغير القابل للتغيير لجهاز الطبقة وهو Blockchain Ethereum. إنها البيئة التي تعيش فيها جميع حسابات Ethereum والعقود الذكية والبيانات. في أي كتلة معينة، يكون للإيثريوم طبقة واحدة فقط مقبولة عالميًا. الآلة الافتراضية لإيثريوم (EVM) هي التي تحدد قواعد حساب الطبقة الصالحة الجديدة من كتلة إلى أخرى.

## حالة الالآت (State Machines)

غالبًا ما يتم وصف سلاسل الكتل مثل Bitcoin على أنها دفاتر موزعة تتيح وجود عملة لا مركزية باستخدام الأدوات الأساسية.

يمكن للعملة المشفرة أن تتصرف مثل العملة "العادية" بسبب القواعد التي تحكم ما يمكن وما لا يمكن فعله لتعديل دفتر الأستاذ. على سبيل المثال، لا يمكن لعنوان Bitcoin أن ينفق المزيد من BTC عما تلقاه سابقًا. تدعم هذه القواعد جميع المعاملات التي تتم على شبكة Bitcoin، وغيرها من شبكات blockchain المماثلة.

في حين أن Ethereum لديها أيضًا عملتها المشفرة الأصلية ETH، فإنها تتيح أيضًا وظيفة أكثر قوة رأيناها - وهي العقود الذكية. بالنسبة لهذه الميزة الأكثر تعقيدًا، نحتاج إلى تشبيه أقوى من مجرد دفتر الأستاذ الموزع.

بدلاً من دفتر الأستاذ الموزع، يمكن وصف إيثريوم بشكل أفضل على أنه آلة حالة افتراضية موزعة.

آلة الحالة (state machine) هي في الأساس أي آلة يمكنها التغيير من حالة إلى أخرى استجابة لمدخلات معينة. مثال على آلة الحالة البسيطة هو الباب الدوار الذي يعمل بقطع النقود المعدنية - البوابة الصغيرة في مترو الأنفاق أو محطات القطار التي تمنعك من دخول المحطة حتى تدفع عملة معدنية أو تنقر على بطاقة تذكرة أو شيء من هذا القبيل.

يحتوي الباب الدوار على حالتين - **مقفل** و **مفتوح**. إن دفع الباب الدوار أثناء وجوده في حالة **القفل** لا يفعل أي شيء ويبقيه في حالة **القفل**. ومع ذلك، إذا قمت بإدخال عملة معدنية، فسوف تتغير الحالة من **مقفل** إلى **غير مقفل**. عند هذه النقطة، لن يؤدي إدخال المزيد من العملات المعدنية إلى أي شيء - وسيبقيها في حالة **إلغاء القفل**. ومع ذلك، بمجرد الضغط عليه للمرور، سيعود إلى حالة **القفل**.

بالنسبة للإيثريوم، الحالة أكثر تعقيدًا من الباب الدوار، لكن المبدأ العام هو نفسه. تقوم الشبكة الشاملة في نهاية اليوم بتخزين كل حالتها في بنية بيانات كبيرة. القواعد المحددة لكيفية تغيير تلك الحالة استجابةً لأنواع مختلفة من المعاملات التي تحدث - والتي يتم تحديدها بواسطة EVM.

<img src="https://www.web3arabs.com/courses/evm.png"/>

## تحولات حالة الايثيريوم

على مستوى عالٍ، يتصرف جهاز EVM بشكل مشابه لوظيفة انتقال الحالة الرياضية (state transition function). بالنظر إلى الحالة الحالية ومجموعة جديدة من المعاملات الصالحة، يمكن أن تنتج حالة جديدة. الناتج حتمي، مما يعني أنه لنفس المدخلات فإنه سينتج دائمًا نفس المخرجات.

يمكن تمثيل هذه الوظيفة على النحو التالي:

<CodeBlock lang="js">
```
Y(S, T) = S'
```
</CodeBlock>

بالنظر إلى الحالة القديمة الصالحة **S** ومجموعة جديدة من المعاملات الصالحة **T**، يمكن لوظيفة انتقال الحالة **Y** أن تنتقل من الحالة **S** إلى الحالة **S'**.

## تعليمات EVM (OPCODE)

يعمل جهاز EVM نفسه كآلة حزم بعمق أقصى يصل إلى 1024 عنصرًا في الحزمة. كل عنصر في تلك الحزمة عبارة عن كلمة بحجم 256 بت (32 بايت).

أثناء تنفيذ المعاملة، يحتفظ بها جهاز EVM بذاكرة مؤقتة لا تستمر بين المعاملات. عندما يبدأ تنفيذ معاملة جديدة، تتم إعادة ضبط الذاكرة المؤقتة.

ومع ذلك، تحافظ العقود الذكية على حالتها الخاصة على blockchain. يشار إلى هذه الحالة عادة باسم التخزين في EVM أثناء تنفيذ المعاملة. أي أن التخزين عبارة عن ذاكرة طويلة المدى للعقود الذكية، والذاكرة هي ذاكرة قصيرة المدى داخل EVM.

يحتوي EVM على منطق موجود يسمح له بتنفيذ بعض رموز EVM OPCODES - العمليات الحسابية الأساسية التي يمكن تنفيذها على البيانات المخزنة مثل **ADD** و **SUB** و **MUL** و **DIV** وما إلى ذلك. كما ينفذ EVM أيضًا عددًا من رموز OPCODES الخاصة بـ Ethereum مثل **BALANCE** و **BLOCKHASH**.

عندما يتم تجميع عقد ذكي في رمز بايت، فإنه يتم تجميعه بشكل أساسي إلى رموز EVM OPCODES هذه. يتم تحويل دوال Solidity عالية المستوى إلى OPCODES منخفضة المستوى التي يمكن لـ EVM فهمها. تعد رموز **OPCODES** هذه هي ما يتم تنفيذه بواسطة العقد حول العالم التي تقوم بتشغيل EVM.

## تطبيقات EVM

يجب أن تلتزم جميع تطبيقات EVM بالمواصفات الموضحة في <a href="https://ethereum.github.io/yellowpaper/paper.pdf" target="_blank">Ethereum Yellowpaper</a>. على مدار تاريخ إيثريوم، خضع EVM للعديد من المراجعات والتحديثات، وتوجد تطبيقات متعددة لـ EVM في لغات البرمجة المختلفة.

يجب أن يتضمن جميع عملاء Ethereum (Geth و Nethermind و Erigon وما إلى ذلك) تطبيق EVM حتى تتمكن العُقد من تنفيذ المعاملات على الشبكة والتحقق منها. بالإضافة إلى ذلك، توجد أيضًا العديد من تطبيقات EVM المستقلة مثل **ethereumjs-evm** و **evmone** و **py-evm** وما إلى ذلك.

## EVM ~= CPU

على أجهزة الكمبيوتر الحديثة، لدينا بالفعل شرائح دقيقة متقدمة تعمل على تشغيل أنظمتنا - أشياء مثل وحدات المعالجة المركزية **Intel 13th Gen** أو شرائح **AMD Ryzen** أو **Apple Silicon**. ومع ذلك، دعونا نلقي نظرة على بعض التصميمات القديمة لوحدة المعالجة المركزية ونرسم تشبيهًا لـ EVM هناك.

وحدة المعالجة المركزية (CPU) هي في الأساس قطعة من الأجهزة التي تحتوي على كمية صغيرة من التخزين المؤقت (سجلات ذاكرة التخزين المؤقت) التي يمكنها استخدامها، ومن ثم يمكنها التواصل مع ذاكرة الوصول العشوائي (RAM) للكمبيوتر الخاص بك والقرص الصلب.

اثناء تشغيل أجهزتك تقوم الرقائق الموجودة في جهاز الكمبيوتر الخاص بك بتفسير الإشارات الكهربائية المختلفة على أنها 0 و 1 (إشارات الجهد المنخفض والعالي) - وتعمل هذه الرقائق 0 و 1 بمثابة تعليمات لهذه الرقائق حول ما يجب القيام به وكيفية التصرف.

بافتراض وجود تصميم كمبيوتر قديم (يبلغ عمره بضعة عقود) حيث كانت بنية وحدة المعالجة المركزية البسيطة أحادية النواة وخيط واحد شائعة - تنفذ وحدة المعالجة المركزية المهام على جهاز الكمبيوتر الخاص بك في تصميم تسلسلي - تعليمات تلو الأخرى. تم تجهيز وحدات المعالجة المركزية هذه لتنفيذ أنواع معينة من التعليمات مع إعطاء الإشارات الكهربائية الصحيحة - ومرة ​​أخرى أشياء بسيطة مثل **ADD** و **SUB** و **MUL** و **DIV** وما إلى ذلك. ومن خلال القيام بهذه العمليات الحسابية، يمكنهم تشغيل برامج رائعة مثل الآلة الحاسبة على جهاز الكمبيوتر الخاص بك.

وحدات المعالجة المركزية (CPUs) اليوم متشابهة، على الرغم من أنها تحتوي على مجموعة أكبر بكثير من التعليمات المتصلة وتعدد النوى والخيوط المتعددة وما إلى ذلك. لكن الفكرة الأساسية تظل كما هي. مجموعة من التعليمات ذات المستوى المنخفض التي يتم دمجها في مجموعة الشرائح لتنفيذ تلك العمليات. كل التعليمات البرمجية ذات المستوى الأعلى التي تكتبها بشكل أساسي في نهاية اليوم سوف تتلخص في مزيج من تلك التعليمات ذات المستوى المنخفض.

تمامًا كما تمثل وحدة المعالجة المركزية بيئة تشغيل لجهاز الكمبيوتر الخاص بك، يمكن اعتبار EVM بمثابة بيئة تشغيل لشبكة Ethereum. جميع التعليمات البرمجية والمعاملات التي تحدث على Ethereum تتلخص في رموز **EVM OPCODES** الأبسط، وEVM هو نوع من وحدة المعالجة المركزية الافتراضية (جهاز افتراضي) يمكنه تنفيذ رموز **OPCODES** هذه، وبالتالي محاكاة نوع ما من وحدة المعالجة المركزية، للسماح لك بالقيام بذلك. أياً كان ما تريد!

## مصادر إضافية

فيما يلي قراءات إضافية اختيارية، ولكن موصى بها، لمعرفة المزيد حول EVM:

- <a href="https://takenobu-hs.github.io/downloads/ethereum_evm_illustrated.pdf" target="_blank">https://takenobu-hs.github.io/downloads/ethereum_evm_illustrated.pdf</a> <br/>
- <a href="https://www.ethervm.io" target="_blank">https://ethervm.io</a> <br/>
- <a href="https://ethereum.github.io/yellowpaper/paper.pdf" target="_blank">https://ethereum.github.io/yellowpaper/paper.pdf</a>

كما هو الحال دائمًا، إذا كانت لديك أي أسئلة أو شعرت بالتعثر أو أردت فقط أن تقول مرحبًا، فقم بالإنضمام على <a href="https://t.me/Web3ArabsDAO" target="_blank">Telegram</a> او <a href="https://discord.gg/ykgUvqMc4Q" target="_blank">Discord</a> وسنكون أكثر من سعداء لمساعدتك!