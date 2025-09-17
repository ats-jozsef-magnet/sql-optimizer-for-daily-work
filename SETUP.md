# Lokális LLM (Mistral) beállítása

Ez a dokumentum a lokális LLM (pl. Mistral) futtatásához ad útmutatót, amely az AI Agent egyik alternatív működési módja.  
A cél, hogy minden feldolgozás **helyben történjen**, így semmilyen adat ne kerüljön külső szolgáltatóhoz.

---

## Előfeltételek
- Operációs rendszer: Linux vagy WSL2 + Ubuntu  
- Python 3.10+  
- GPU esetén CUDA támogatás (ajánlott, de CPU-only módban is futtatható)  
- Git telepítve

---

## Telepítés lépésekben

1. **Virtuális környezet létrehozása**
   ```bash
   python -m venv venv
   source venv/bin/activate
