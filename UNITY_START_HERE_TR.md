# NightShift — Unity varlık paketi

## Kurulum
1. Unity projenizi yedekleyin. Built-in veya URP kullanan Unity 6 / 2022.3 projesinde `NightShiftThief_Unity.unitypackage` dosyasını açın ve Import seçin.
2. Script derlemesinin bitmesini bekleyin.
3. `Tools > Night Shift > Install Current Asset Package` menüsünü çalıştırın.
4. Oluşturulan prefablar: `Assets/NightShiftThief/Generated/Prefabs`.
5. Model ve animasyon FBX'leri zaten pakettedir. Kurulum aracı materyalleri, Animator Controller'ları, prefabları ve ölüm ragdoll bağlantılarını sizin Unity projenizde üretir.

Bu bilgisayarda çalıştırılabilir Unity Editor bulunmadığından paket Unity içinde derlenip oynatılmadı. Kurulum çıktıları önceden üretilmiş gibi kabul edilmemeli. Konsolda hata olursa hata metni ve Unity sürümüyle devam edin. Araç mevcut üretilmiş prefabları bulursa üzerine yazmaz. HDRP materyalleri elle uyarlanmalıdır.

## İçerik
- 82 güncel animasyon klibi; 30 FPS. Eski animasyon sürümleri ve PREVIEW klipleri dışarıda bırakıldı.
- 33 model dosyası: karakter, detaylı FP kollar, eşya taşıma varyantları ve 11 bağımsız eşya.
- Normal hareket, gizli yürüyüş, koşma, çömelme, yan adım, zıplama, çuval taşıma/açma/koyma/kapatma.
- FP boş el ve fener hareketleri; mücevher tutma/çıkarma; iki elle altın/kasa/kemik tutma, çıkarma ve FP yürüme sallantısı.
- Atlas dokusu, materyal renkleri/parlaklıkları, dar açılı ele bağlı fener ışığı için kurulum.

`ThirdPerson` karakter; `FirstPerson` boş ellerdir. `FPJewelry_*` ve `FPTwoHand_*` kameraya takılan el/eşya varyantlarıdır. `TPJewelry_*` ve `TPTwoHand_*` dışarıdan görünüş içindir. `LOOT_*` ve `ITEM_*_Pickup` bağımsız fiziksel dünya eşyalarıdır. Tutulan modellerde Rigidbody yoktur; dünya prefablarında kutu collider ve Rigidbody kurulur.

## First person
FP prefabını kameranın altına yerleştirin ve local position/rotation sıfır, scale bir yapın. Prefab içindeki modelin aşağı ofsetini sıfırlamayın. Referans görüş açısı yatay 85°, 16:9 için Unity Camera dikey FOV yaklaşık 54.5°'dir. Başka FOV/aspect değerlerinde ekran kaplama değişir.
Yalnızca bir FP varyantı açık olsun. Yerel oyuncunun tam gövdesini FP kamerasından gizleyin; diğer oyuncular TP modeli görsün. Kamera/layer/culling ayarlarını projenize göre yapın.

`NightShiftClipPlayer.PlayClip("tam_klip_adı")` seçilen klibe geçer. `SetMoving(true/false)` mevcut yürüme/tutma klibini seçer. `Raise()` çıkarma klibini başlatır; çıkarma sonunda tutmaya otomatik geçiş kurulur. Koşma/zıplama/yön/death kararlarını oyuncu kodu vermelidir. Eşya çıkarılırken görünürdür. Mücevher ve iki-el TP tutuşları tam yürüyüş animasyonu değildir; gövde animasyonuna katman/IK entegrasyonu gerekir. Mücevher FP için ayrıca yürüme klibi üretilmedi.

## Çuval ve ölüm
Ana karakterde `SackEquipment.SetEquipped(bool)` görselleri ve normal/taşıma klip eşlemelerini değiştirir. Çuval etkileşimi için Sack_Open -> Sack_Open_Idle -> Sack_Insert_Item -> Sack_Open_Idle -> Sack_Close sırası oyundan sürülür. Klip olayları otomatik atanır; envanter aktarımını `SackInteractionEvents` UnityEvent'lerine bağlayın. Hareketi etkileşim boyunca durdurun.
Ragdoll yalnız ölümde `ThiefRagdoll.DieWithVelocity(hız)` ile açılır. Oyuncu kapsülü, hareket bileşenleri ve FP kolları ilgili alanlara oyun projesinde atanmalıdır. Aksesuar spring scriptleri opsiyoneldir; bake edilmiş harekete ek olarak otomatik açılmazlar. Çuvalı bırakma ve envanter davranışları oyun koduna aittir.

## Sınırlar
Generic rig kullanılır; Humanoid retarget kurulumu yapılmaz. Kök hareketi kapalıdır; yer değiştirme ve zıplama fiziğini oyun yönetir. Ayrı normal standing-idle animasyonu yapılmadı: ana karakterin varsayılan durumu `Neutral_NoAuthoredIdle` olup dinlenme pozudur. Fener ve FP varyantlarının ayrı idle'ları vardır. TP carry klipleri, eğimler, geçişler, collider ölçüleri ve farklı FOV'lar hedef projede ayarlanmalıdır. Otomatik ağ, envanter, input veya tam oyun kontrolcüsü yoktur.

## Diğer AI / geliştirici için
`Data/catalog.json` güncel FBX/model/klip listesidir. `*_authoring.json` Blender tasarım notlarıdır; eski “review/no export” ifadeleri bu notların tarihsel durumudur, paket durumunu belirlemez. Blender kaynağı GitHub deposunun kökündeki `NightShift_Thief.blend` dosyasıdır. Kaynağı Unity Assets içine koymayın; FBX'leri kullanın.

Unity API referansları: https://docs.unity3d.com/ScriptReference/ModelImporterClipAnimation.html ve https://docs.unity3d.com/ScriptReference/Animations.AnimatorController.CreateAnimatorControllerAtPath.html
