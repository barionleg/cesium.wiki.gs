Note: In the below steps, replace `<collada2json>` with the location of your git repository.  Also, in step 12, change `Release` to `Debug` if you are building `Debug`

1. `cd <collada2json>\converter\dae2json\dependencies\OpenCOLLADA`
2. `mkdir VisualStudio10`
3. `cd VisualStudio10`
4. `cmake -G "Visual Studio 10" ..`
5. Open OPENCOLLADA.sln
6. Select Release or Debug
7. Build `buffer_static`, `ftoa_static`, `pcre`, `UTF_static`, and `xml` projects.
8. Modify <collada2json>\converter\dae2json\dependencies\OpenCOLLADA\CMakeLists.txt
```
CHANGE
add_subdirectory(${EXTERNAL_LIBRARIES}/UTF)
add_subdirectory(${EXTERNAL_LIBRARIES}/MathMLSolver)

TO
add_subdirectory(Externals/UTF)
add_subdirectory(Externals/MathMLSolver)
```
9. `cd <collada2json>\converter\dae2json`
10. `mkdir VisualStudio10`
11. `cd VisualStudio10`
12. cmake -DLIBXML2_INCLUDE_DIR=`<collada2json>`\converter\dae2json\dependencies\OpenCOLLADA\Externals\LibXML\include\ -DLIBXML2_LIBRARIES=`<collada2json>`\converter\dae2json\dependencies\OpenCOLLADA\VisualStudio10\lib\Release\xml.lib -DPCRE_INCLUDE_DIR=`<collada2json>`\converter\dae2json\dependencies\OpenCOLLADA\Externals\pcre\include -DPCRE_LIBRARIES=`<collada2json>`\converter\dae2json\dependencies\OpenCOLLADA\VisualStudio10\lib\Release\pcre.lib -G "Visual Studio 10" ..
13. open COLLADA2JSON.sln
14. Select Release or Debug
15. `OpenCOLLADABaseUtils_static` -> properties -> C/C++ -> Preprocessor -> Add PCRE_STATIC
16. `OpenCOLLADASaxFrameworkLoader_static` -> properties -> C/C++ -> Preprocessor -> Add PCRE_STATIC
17. Build `collada2json`