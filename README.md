
# Flowbite Datepicker Türkçe Desteği

Flowbite Datepicker bileşenine Türkçe dil desteği ekler. Bu, kullanıcıların tarih seçici bileşenini Türkçe dilinde kullanabilmelerini sağlar.

## Özellikler
- Haftanın günleri ve ay isimleri Türkçe olarak görüntülenir.
- Bugün, temizleme (clear) butonları ve tarih formatı Türkçeleştirilmiştir.
- Haftanın ilk günü Pazartesi olarak ayarlanmıştır.



## Kullanım

JavaScript dosyanızda, aşağıdaki kodu ekleyin:

```js
window.addEventListener("load", () => {
    setTimeout(() => {
        let locales = {
            tr: {
                days: ["Pazar", "Pazartesi", "Salı", "Çarşamba", "Perşembe", "Cuma", "Cumartesi"],
                daysShort: ["Paz.", "Pzt.", "Sal.", "Çar.", "Per.", "Cum.", "Cmt."],
                daysMin: ["Pz.", "Pt.", "Sa.", "Ça.", "Pe.", "Cu.", "Ct."],
                months: ["Ocak", "Şubat", "Mart", "Nisan", "Mayıs", "Haziran", "Temmuz", "Ağustos", "Eylül", "Ekim", "Kasım", "Aralık"],
                monthsShort: ["Oca.", "Şub.", "Mar.", "Nis.", "May.", "Haz.", "Tem.", "Ağu.", "Eyl.", "Eki.", "Kas.", "Ara."],
                today: "Bugün",
                weekStart: 1,
                clear: "Temizle",
                format: "dd.mm.yyyy"
            }
        };
        let flowbitePickers = Object.values(FlowbiteInstances.getInstances("Datepicker")).map((instance) => {
            return instance.getDatepickerInstance();
        });
        for (const flowbitePicker of flowbitePickers) {
            for (const picker of flowbitePicker.datepickers || [flowbitePicker]) {
                Object.assign(picker.constructor.locales, locales);
                picker.setOptions({ language: "tr" });
            }
        }
    }, 100);
});
```