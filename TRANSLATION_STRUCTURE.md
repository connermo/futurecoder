I'll help analyze how the program handles language files. Let me search for relevant files and scripts:

Search files...
Let me analyze the translation system structure. I'll also check for any additional relevant files:

Ran tool
Ran tool
Based on the analysis, here's how the language/translation system works:

1. **Core Translation Files and Structure**:
   - `/translations/locales/` - Contains language-specific directories (en, es, fr, zh, etc.)
   - `/translations/locales/{lang}/LC_MESSAGES/futurecoder.mo` - Compiled translation files for each language
   - `/translations/english.po` - Source translation file for English
   - `/translations/codes.json` - Contains code block translations
   - `/translations/manual_programs.json` - Contains manually translated program examples

2. **Key Scripts and Files**:
   - `core/translation.py` - Main translation handling module
     - Uses Python's `gettext` for translation management
     - Handles language switching via `set_language()`
     - Manages code block translations
   
   - `translations/generate_po_file.py` - Generates translation files
     - Creates `.po` files for translation
     - Handles special translation cases (code blocks, predictions, etc.)
     - Generates `codes.json` for code translations
   
   - `translations/get_manual_programs.py` - Extracts manually translated programs
     - Processes `.mo` files to find program translations
     - Generates `manual_programs.json`

   - `scripts/generate_static_files.py` - Handles translation file packaging
     - Includes translation files in the build
     - Packages language-specific files into `python_core.tar`

3. **Translation Process**:
   a. **Source Generation**:
      - English text is extracted into `english.po`
      - Code blocks are handled separately in `codes.json`
      - Special program examples are in `manual_programs.json`

   b. **Translation**:
      - Translators work with `.po` files
      - Translations are compiled into `.mo` files
      - Code translations are managed separately

   c. **Build Process**:
      - Translation files are packaged into the build
      - Language-specific files are included in `python_core.tar`
      - Frontend terms are handled separately in `frontend/src/english_terms.json`

4. **Special Translation Features**:
   - Code blocks can be auto-translated or manually translated
   - Special markers like `__codeN__` for code blocks
   - Format strings with variables (e.g., `{max_count}`)
   - Frontend-specific translations
   - Support for manual program translations

5. **Language Support**:
   Currently supported languages (in `/translations/locales/`):
   - English (en)
   - Spanish (es)
   - Spanish Latin America (es-latam)
   - French (fr)
   - Polish (pl)
   - Chinese (zh)
   - Tamil (ta)
   - Brazilian Portuguese (br)

6. **Integration Points**:
   - `core/init_pyodide.py` - Initializes language settings
   - Frontend integration through `english_terms.json`
   - Build system integration through `generate_static_files.py`

Would you like me to dive deeper into any particular aspect of the translation system? For example:
1. How code translations work
2. The build process for translations
3. How to add a new language
4. How frontend translations are handled
5. The translation workflow for contributors