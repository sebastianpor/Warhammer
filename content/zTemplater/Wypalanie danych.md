<%*
// Pobierz zawartość pliku
const file = tp.file.find_tfile(tp.file.path(true));
const content = await app.vault.read(file);

// Pobierz dane z nagłówka (YAML)
const fm = app.metadataCache.getFileCache(file)?.frontmatter;

if (fm) {
    // Funkcja zamieniająca kod na wartość
    const newContent = content.replace(/`=this\.(.*?)`/g, (match, key) => {
        
        // Sprawdź, czy klucz w ogóle istnieje w nagłówku
        if (fm[key] !== undefined) {
            let val = fm[key];

            // LOGIKA NAPRAWSTA: Jeśli wartość to null (puste) lub pusty tekst -> zamień na myślnik
            if (val === null || val === "") {
                val = "-";
            }
            
            // Zwróć wartość (lub myślnik) + dwie spacje na końcu
            return val + "  "; 
            
        } else {
            // Opcjonalnie: Jeśli klucza w ogóle nie ma w YAML, też wstaw myślnik (żeby nie było błędów)
            // Jeśli wolisz widzieć błąd, usuń poniższą linię i odkomentuj "return match"
            return "-  "; 
            
            // new Notice(`❌ Brak pola "${key}" w nagłówku!`);
            // return match; 
        }
    });

    // Zapisz plik
    if (content !== newContent) {
        await app.vault.modify(file, newContent);
        new Notice("✅ Dane wypalone (z myślnikami i odstępami)!");
    } else {
        new Notice("ℹ️ Brak zmian do wprowadzenia.");
    }
} else {
    new Notice("⚠️ Ten plik nie ma nagłówka YAML.");
}
%>