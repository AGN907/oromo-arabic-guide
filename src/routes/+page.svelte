<script>

  import Clock from 'lucide-svelte/icons/clock';
  import Home from 'lucide-svelte/icons/house';
  import Search from 'lucide-svelte/icons/search';
  import Shirt from 'lucide-svelte/icons/shirt';
  import Sparkles from 'lucide-svelte/icons/sparkles';
  import Utensils from 'lucide-svelte/icons/utensils';
  import { quintOut } from 'svelte/easing';
import { crossfade } from 'svelte/transition';

  // Svelte 5 State (Runes)
  let activeTab = $state('greetings');
  let searchTerm = $state('');

 const [send, receive] = crossfade({
    duration: 700,
    easing: quintOut
  });

  const data = {
    greetings: {
      title: 'التحيات والأوقات',
      icon: Clock,
      color: 'from-purple-500 to-pink-500',
      items: [
        { ar: 'صباح الخير', desc: 'تحية الصباح', oromo: 'Akkam bulte' },
        { ar: 'صباح النور', desc: 'الرد على صباح الخير', oromo: 'Akkam bulte' },
        { ar: 'مساء الخير', desc: 'تحية المساء', oromo: 'Akkam ooltan' },
        { ar: 'مساء النور', desc: 'الرد على مساء الخير', oromo: 'Akkam ooltan' },
        { ar: 'تصبحون على خير', desc: 'قبل النوم', oromo: 'Halkan gaarii' },
        { ar: 'وأنتم من أهله', desc: 'الرد على تصبحون على خير', oromo: 'Ati immoo maatii isaa keessaa jirta' },
        { ar: 'صباح', desc: 'وقت الصباح', oromo: 'ganama' },
        { ar: 'ظهر', desc: 'وقت الظهيرة', oromo: 'dugda' },
        { ar: 'المساء', desc: 'وقت المساء', oromo: 'galgala' },
        { ar: 'ليل', desc: 'وقت الليل', oromo: 'halkan' },
        { ar: 'الفجر', desc: 'وقت صلاة الفجر', oromo: 'barii' }
      ]
    },
    rooms: {
      title: 'أقسام ومرافق المنزل',
      icon: Home,
      color: 'from-blue-500 to-cyan-500',
      items: [
        { ar: 'غرفة النوم', desc: 'مكان النوم', oromo: 'kutaa ciisichaa' },
        { ar: 'غرفة العيال', desc: 'غرفة الأطفال', oromo: 'Kutaa ijoollee' },
        { ar: 'مجلس الرجال', desc: 'صالة الضيوف (رجال)', oromo: 'Mana Maree Dhiiraa' },
        { ar: 'مجلس النساء', desc: 'صالة الضيوف (نساء)', oromo: 'Mana Maree Dubartootaa' },
        { ar: 'غرفة الطعام', desc: 'غرفة الأكل', oromo: 'Kutaa nyaataa' },
        { ar: 'الديوانية', desc: 'مجلس خارجي', oromo: 'Mana Maree Alaa (Diwaaniyaa)' },
        { ar: 'المطبخ', desc: 'مكان الطبخ', oromo: 'mana nyaataa' },
        { ar: 'الحوش', desc: 'الفناء الخارجي', oromo: 'Mooraa' },
        { ar: 'الحمام', desc: 'دورة المياه', oromo: 'mana fincaanii' },
        { ar: 'المسبح', desc: 'بركة السباحة', oromo: 'poolii daakuu' },
        { ar: 'الممر', desc: 'السيب / الكوريدور', oromo: 'koridoorii' },
        { ar: 'الدرج', desc: 'السلالم', oromo: 'Gulantaa' }
      ]
    },
    furniture: {
      title: 'الأثاث والأدوات',
      icon: Home,
      color: 'from-green-500 to-emerald-500',
      items: [
        { ar: 'مخدات', desc: 'وسائد', oromo: 'barcumaa' },
        { ar: 'زولية', desc: 'سجاد', oromo: 'Kaarpeetiiwwan' },
        { ar: 'شماعة', desc: 'تعليق الملابس', oromo: 'Uffata fannifame' },
        { ar: 'زبالة', desc: 'حاوية النفايات', oromo: 'kosii' },
        { ar: 'سلة ملابس', desc: 'سلة الغسيل', oromo: 'baaskitii miiccaa miiccaa' },
        { ar: 'منشفة', desc: 'فوطة', oromo: 'fooxaa' },
        { ar: 'صابون', desc: 'للتنظيف', oromo: 'saamuunaa' },
        { ar: 'فرشة أسنان', desc: 'لتنظيف الأسنان', oromo: 'buruushiin ilkaanii' },
        { ar: 'معجون أسنان', desc: 'معجون', oromo: 'shaampoo ilkaanii' }
      ]
    },
    appliances: {
      title: 'الأجهزة الكهربائية',
      icon: Sparkles,
      color: 'from-yellow-500 to-orange-500',
      items: [
        { ar: 'الثلاجة', desc: 'حفظ الطعام', oromo: 'kottolleessaa' },
        { ar: 'المايكرويف', desc: 'تسخين الطعام', oromo: 'nyaata ho\'isuu' },
        { ar: 'الفرن الكهربائي', desc: 'للطبخ', oromo: 'foonni elektirikii' },
        { ar: 'الخلاط', desc: 'للعصير', oromo: 'blender jedhamuun beekama' },
        { ar: 'القلاية', desc: 'للقلي', oromo: 'fryer kan jedhu' },
        { ar: 'محمصة الخبز', desc: 'للتوست', oromo: 'daabboo toaster' },
        { ar: 'غلاية الموية', desc: 'لتسخين الماء', oromo: 'Keella bishaanii' },
        { ar: 'الغسالة', desc: 'لغسل الملابس', oromo: 'maashinii miiccaa' },
        { ar: 'الكواية', desc: 'لكي الملابس', oromo: 'sibiila' },
        { ar: 'المكنسة', desc: 'للتنظيف', oromo: 'haraa' },
        { ar: 'مكيف', desc: 'تبريد الجو', oromo: 'qilleensa to\'atu' }
      ]
    },
    kitchen: {
      title: 'أدوات المطبخ والمقادير',
      icon: Utensils,
      color: 'from-red-500 to-pink-500',
      items: [
        { ar: 'ملعقة صغيرة', desc: 'للشاي / الحلا', oromo: 'kanastaa shaayii' },
        { ar: 'ملعقة كبيرة', desc: 'للشوربة / الأكل', oromo: 'kanastaa' },
        { ar: 'شوكة', desc: 'للأكل', oromo: 'shukkaa' },
        { ar: 'سكين', desc: 'للتقطيع', oromo: 'haaduu' },
        { ar: 'قدر', desc: 'وعاء الطبخ', oromo: 'hamma' },
        { ar: 'مقلاة', desc: 'طاوة القلي', oromo: 'frying pan jedhamu' },
        { ar: 'بصل', desc: 'خضار', oromo: 'qullubbii diimaa' },
        { ar: 'طماطم', desc: 'خضار', oromo: 'timaatima' },
        { ar: 'بطاطس', desc: 'خضار', oromo: 'boqqolloo' },
        { ar: 'رز', desc: 'طعام أساسي', oromo: 'ruuzii' },
        { ar: 'زيت', desc: 'للطبخ', oromo: 'dibata' },
        { ar: 'ملح', desc: 'بهارات', oromo: 'soogidda' },
        { ar: 'دجاج', desc: 'لحوم', oromo: 'hanqaaquu' },
        { ar: 'لحم', desc: 'لحوم', oromo: 'foon' },
        { ar: 'حليب', desc: 'ألبان', oromo: 'aannan' },
        { ar: 'خبز', desc: 'مخبوزات', oromo: 'daabboo' }
      ]
    },
    clothes: {
      title: 'الملابس',
      icon: Shirt,
      color: 'from-indigo-500 to-purple-500',
      items: [
        { ar: 'فنيلة داخلية', desc: 'ملابس رجالية', oromo: 'shamizii jalaa' },
        { ar: 'جلابية', desc: 'ملابس نسائية', oromo: 'Jalabiyaa' },
        { ar: 'بجامة', desc: 'ملابس نوم', oromo: 'uffata hirribaa' }
      ]
    },
    commands: {
      title: 'تعليمات العمل اليومية',
      icon: Sparkles,
      color: 'from-teal-500 to-green-500',
      items: [
        { ar: 'نظفي البيت', desc: 'تنظيف شامل للمنزل', oromo: 'Qulqullina manaa gadi fageenyaan' },
        { ar: 'نظفي الغرفة ورتبي السرير', desc: 'ترتيب غرفة النوم', oromo: 'Kutaa qulqulleessi siree tolchi' },
        { ar: 'أمسحي المرآة', desc: 'تلميع الزجاج والمرايا', oromo: 'Glass fi mirror polishing gochuu' },
        { ar: 'نظفي مجلس الرجال', desc: 'تنظيف غرفة الضيوف', oromo: 'Qulqullina kutaa keessummootaa' },
        { ar: 'نظفي الدرج', desc: 'كنس ومسح السلالم', oromo: 'Baafata qulqulleessi' },
        { ar: 'نظفي الحوش', desc: 'غسيل الفناء الخارجي', oromo: 'Mooraa qulqulleessi' },
        { ar: 'نظفي الزولية', desc: 'كنس السجاد', oromo: 'Kaarpeeti qulqulleessuu' },
        { ar: 'أحضري منظف الزولية', desc: 'جلب أدوات التنظيف', oromo: 'Meeshaalee qulqulleessituu fidaa' },
        { ar: 'أنفضي الغبار', desc: 'إزالة الغبار عن الأثاث', oromo: 'Meeshaalee manaa dafqa itti naquu' },
        { ar: 'غيري أكياس المخدات', desc: 'استبدال أغطية الوسائد', oromo: 'Barcuma jijjiiri' },
        { ar: 'نظفي الجدار', desc: 'مسح الجدران المتسخة', oromo: 'Dallaa qulqulleessi' },
        { ar: 'نظفي الطاولة', desc: 'مسح الطاولات', oromo: 'Minjaala qulqulleessi' },
        { ar: 'نظفي المغسلة', desc: 'غسيل حوض اليدين', oromo: 'Meeshaa harkaa dhiqachuu' },
        { ar: 'نظفي المرحاض', desc: 'تعقيم الكرسي', oromo: 'Mana fincaanii qulqulleessuu' },
        { ar: 'جهزي المنشفة', desc: 'وضع فوطة نظيفة', oromo: 'Haalluu qopheessaa' },
        { ar: 'إفتحي الغاز', desc: 'تشغيل الموقد', oromo: 'Gaazii sana qabsiisi' },
        { ar: 'طفي الغاز', desc: 'إطفاء الموقد', oromo: 'Gaazii dhaamsaa' },
        { ar: 'غسلي الصحون', desc: 'جلي الأواني', oromo: 'Mi\'a nyaataa dhiqadhaa' },
        { ar: 'غسلي القدر', desc: 'تنظيف أواني الطبخ', oromo: 'Meeshaalee nyaata itti bilcheessan qulqulleessuu' },
        { ar: 'حطي القدر على النار', desc: 'بدء الطبخ', oromo: 'Qodaa sana ibidda irra kaa\'i' },
        { ar: 'شوحي اللحم', desc: 'قلي اللحم قليلا', oromo: 'Foon salphaatti bilcheessi' },
        { ar: 'أطبخي البيض', desc: 'إعداد البيض (قلي/سلق)', oromo: 'Hanqaaquu qopheessuu (frying/boiling)' },
        { ar: 'سوي شاي', desc: 'إعداد الشاي', oromo: 'Shaayii tolchuu' },
        { ar: 'سوي قهوة', desc: 'إعداد القهوة', oromo: 'Buna tolchuu' },
        { ar: 'أغلي الموية', desc: 'تسخين الماء', oromo: 'Bishaan sana bilcheessi' },
        { ar: 'قشري البطاطس', desc: 'إزالة القشر', oromo: 'Boqqolloo sana gogaa irraa baasuu' },
        { ar: 'قطعي البصل', desc: 'تقطيع صغير', oromo: 'Baqalaa muraa' },
        { ar: 'جهزي السفرة', desc: 'إعداد طاولة الطعام', oromo: 'Minjaala nyaataa qopheessuu' },
        { ar: 'حضري بيالات الشاي', desc: 'تجهيز أكواب الشاي', oromo: 'Shaayii qopheessaa' },
        { ar: 'حضري طفرية القهوة', desc: 'تجهيز صينية القهوة', oromo: 'Saanii bunaa qopheessuu' }
      ]
    },
    schedule: {
      title: 'الجدول اليومي',
      icon: Clock,
      color: 'from-rose-500 to-red-500',
      items: [
        { ar: 'الصباح الباكر', desc: 'الاستيقاظ والاستعداد', oromo: 'Shawaari fudhachuu, ilkaan buruushiin dhiqachuu, wudu\'uu fi ciree nyaachuu' },
        { ar: 'فترة الصباح', desc: 'تنظيف المجالس', oromo: 'Kutaa taa\'umsaa dhiiraa fi dubartootaa tartiibaan qulqulleessuu' },
        { ar: 'فترة الصباح', desc: 'تنظيف الغرف', oromo: 'Kutaa nyaataa qulqulleessi, achiis kutaa ijoollee' },
        { ar: 'الضحى', desc: 'تنظيف الجناح الرئيسي', oromo: 'Haati manaa erga dammaqxee booda kutaa guddichaa fi mana fincaanii isaa qulqulleessite' },
        { ar: 'قبل الظهر', desc: 'المطبخ', oromo: 'Laaqana qopheessuuf gargaaruuf gara kutaa nyaataa seeni' },
        { ar: 'بعد الظهر', desc: 'الغداء', oromo: 'Haadha manaa gargaaruu, laaqana tajaajiluu' },
        { ar: 'بعد الغداء', desc: 'التنظيف', oromo: 'Minjaala qulqulleessuu fi mi\'a dhiqachuu' },
        { ar: 'المساء', desc: 'تنظيف المطبخ', oromo: 'Kushiinaa gadi fageenyaan qulqulleessuu fi lafa isaa dhiqachuu' },
        { ar: 'قبل النوم', desc: 'التأكد من البيت', oromo: 'Balballi cufamee fi manni qulqulluu ta\'uu isaa mirkaneessi' },
        { ar: 'حسب الحاجة', desc: 'غسيل الملابس', oromo: 'Halluu addaan baasuu (adii/halluu), dhiqachuu, gogsuu' },
        { ar: 'حسب الحاجة', desc: 'كي الملابس', oromo: 'Uffanni erga goge fi kaazinaa keessatti fannifamee booda sibiila kaa\'i' }
      ]
    }
  };

  const tabs = [
    { id: 'greetings', label: 'التحيات' },
    { id: 'rooms', label: 'المنزل' },
    { id: 'furniture', label: 'الأثاث' },
    { id: 'appliances', label: 'الأجهزة' },
    { id: 'kitchen', label: 'المطبخ' },
    { id: 'clothes', label: 'الملابس' },
    { id: 'commands', label: 'التعليمات' },
    { id: 'schedule', label: 'الجدول اليومي' }
  ];

  // Derived Values (Svelte 5)
  let currentData = $derived(data[activeTab]);
  
  let filteredItems = $derived(currentData.items.filter(item =>
    item.ar.includes(searchTerm) ||
    item.desc.includes(searchTerm) ||
    item.oromo.toLowerCase().includes(searchTerm.toLowerCase())
  ));
</script>

<div class="min-h-screen bg-gradient-to-br from-slate-50 to-slate-100" dir="rtl">
  <div class="container p-6 mx-auto max-w-7xl">
    <!-- Header -->
    <div class="mb-8 text-center">
      <h1 class="pb-2 mb-3 text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-indigo-600 to-purple-600">
        دليل تعليم لغة الأورومو
      </h1>
      <p class="text-lg text-slate-600">قاموس شامل للكلمات والجمل اليومية - عربي / أورومو</p>
    </div>

    <!-- Search Bar -->
    <div class="relative mb-6">
      <Search class="absolute top-3.5 right-4 text-slate-400" size={20} />
      <input
        type="text"
        placeholder="ابحث عن كلمة بالعربي أو الأورومو..."
        bind:value={searchTerm}
        class="py-3 pr-12 pl-4 w-full rounded-xl border-2 shadow-sm transition-all focus:border-indigo-500 focus:outline-none border-slate-200"
      />
    </div>

    <!-- Tabs -->
  <div class="flex flex-wrap gap-2 p-3 mb-6 bg-white rounded-xl shadow-md">
      {#each tabs as tab (tab.id)}
        <button
          onclick={() => activeTab = tab.id}
          class={`relative px-6 py-2.5 rounded-lg font-semibold transition-all duration-300 ${
            activeTab === tab.id
              ? 'text-white scale-105'
              : 'bg-slate-100 text-slate-600 hover:bg-slate-200'
          }`}
        >
          {#if activeTab === tab.id}
            <div
              in:receive={{ key: 'active-tab' }}
              out:send={{ key: 'active-tab' }}
              class={'absolute inset-0 rounded-lg shadow-lg bg-gradient-to-r ' + data[tab.id].color}
            ></div>
          {/if}
          <span class="relative z-10">{tab.label}</span>
        </button>
      {/each}
    </div>

    <!-- Content Header -->
    <div class={`bg-gradient-to-r ${currentData.color} rounded-xl p-6 mb-6 text-white shadow-lg`}>
      <div class="flex gap-4 items-center">
        <div class="p-3 rounded-lg bg-white/20 backdrop-blur-sm">
          <currentData.icon class="size-12" />
        </div>
        <div>
          <h2 class="text-3xl font-bold">{currentData.title}</h2>
          <p class="mt-1 text-white/90">عدد العناصر: {filteredItems.length}</p>
        </div>
      </div>
    </div>

    <!-- Content Grid -->
    <div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-3">
      {#each filteredItems as item, index}
        <div class="p-5 bg-white rounded-xl border-2 shadow-md transition-all duration-500 hover:shadow-xl hover:-translate-y-1 border-slate-100">
          <div class="flex justify-between items-start mb-3">
            <h3 class="text-xl font-bold text-slate-800">{item.ar}</h3>
            <span class={`px-3 py-1 rounded-full text-xs font-semibold bg-gradient-to-r ${currentData.color} text-white`}>
              {index + 1}
            </span>
          </div>
          <p class="mb-3 text-sm italic text-slate-600">{item.desc}</p>
          <div class="p-3 bg-gradient-to-r rounded-lg border-r-4 border-indigo-500 from-slate-50 to-slate-100">
            <p class="text-lg font-semibold text-indigo-700">{item.oromo}</p>
          </div>
        </div>
      {/each}
    </div>

    {#if filteredItems.length === 0}
      <div class="py-16 text-center">
        <div class="mb-4 text-6xl">🔍</div>
        <p class="text-xl text-slate-500">لم يتم العثور على نتائج</p>
      </div>
    {/if}

    <!-- Footer -->
    <div class="p-6 mt-12 text-center bg-white rounded-xl shadow-md">
      <p class="text-slate-600">
        <span class="font-semibold text-indigo-600">إجمالي الكلمات والجمل:</span> 
        {Object.values(data).reduce((acc, cat) => acc + cat.items.length, 0)}
      </p>
    </div>
  </div>
</div>
