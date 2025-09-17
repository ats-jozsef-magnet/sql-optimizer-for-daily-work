# AI-alapú SQL támogatás Delphi fejlesztéshez

## Szerző
**József Áts**  
Email: ats.jozs@gmail.com  
GitHub: [github.com/ats-jozsef-magnet](https://github.com/ats-jozsef-magnet)

---

## Projekt célja
A projekt célja, hogy támogassa a Delphi-ben fejlesztett alkalmazásokban használt SQL utasítások hatékony kezelését és optimalizálását mesterséges intelligencia (AI) segítségével.  
A megoldás két, egymástól független folyamatra épül:

1. **Forráskód-alapú SQL kinyerés és átalakítás**  
   - Az IDE: **Visual Studio Code (VS Code)**.  
   - Egy AI Agent automatikusan feldolgozza a Git working directory még nem commit-ált fájljait (Git diff alapján).  
   - Az érintett Delphi `.pas` és `.dfm` fájlokból kinyeri a teljes SQL utasításokat, még akkor is, ha csak kis részletük módosult.  
   - Az AI Agent az SQL-eket önállóan futtatható script formátumra alakítja.

2. **SQL-optimalizálás és indexjavaslatok**  
   - Egy manuálisan megadott SQL utasítást az AI Agent átvizsgál, és javaslatokat tesz:
     - optimalizált lekérdezésre,
     - szükséges indexekre.  
   - Elfogadás esetén az AI a DDL scriptet is legenerálja.  
   - A script futtatása vagy a javított SQL visszaültetése a forráskódba manuálisan történik.

---

## AI Agent működési lehetőségek

### 1. OpenAI ChatGPT Team előfizetéssel
- A feldolgozott SQL-eket és kódokat **anonimizálva** küldi ki, így minimálisra csökkentve a rendszerre vonatkozó információk kiszivárgását.  
- A diff előfeldolgozás és az anonimizálás **lokálisan történik** (pl. azonosítók, táblanevek hash-elése vagy álnevesítése).  
- Közbenső manuális ellenőrzéssel teljesen elérhető, hogy **0 metaadat** kerüljön kiküldésre.

### 2. Lokális LLM (pl. Mistral)
- A feldolgozás **teljesen helyben történik**, így nincs adatküldés külső szolgáltatóhoz.  
- Kisebb, 30B paraméterszám alatti modellek (pl. Mistral 7B/8x7B) elegendőek a feladatra.  
- Erőforrásigény: dedikált GPU vagy jól optimalizált CPU környezet.  
- Telepítési és futtatási lépések a `SETUP.md` fájlban találhatók.

---

## Főbb előnyök
- Automatizált SQL-kinyerés és script-készítés.  
- AI által támogatott, kontextus-alapú optimalizálás.  
- Két működési mód: felhőalapú (ChatGPT Team, anonimizálással) vagy teljesen lokális (Mistral).  
- Manuális ellenőrzési pontok beépítve, így a fejlesztő dönt az élesítésről.

---

## Lehetséges továbbfejlesztések
- Több LLM támogatása (pl. LLaMA, Claude).  
- Intelligensebb SQL összehasonlító és diff-kezelő modul.  
- Automatikus dokumentáció-generálás a javasolt optimalizációkhoz.

---

## Használati forgatókönyv (példa)

1. **Fejlesztői munka közben**:  
   - SQL változtatás történik egy Delphi forrásfájlban.  
   - Git diff alapján az AI Agent kinyeri és átalakítja az SQL-t.  

2. **Optimalizálás**:  
   - A fejlesztő manuálisan betölti az SQL-t az AI Agent moduljába.  
   - Az AI javaslatot tesz indexre vagy módosított lekérdezésre.  

3. **Érvényesítés**:  
   - A fejlesztő manuálisan futtatja a DDL vagy SQL scriptet az adatbázis adminisztrációs eszközében.  

---

## Licenc
MIT License
