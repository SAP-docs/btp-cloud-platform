<!-- loio57013a7759d34d13b0cca4aa23db02d0 -->

# PDF Merger API

You can use a class-based API to merge the content of different PDF files into a single PDF file. The result file contains all pages of the source files in the sequence of the original files.

If you want to merge PDF files, you require an instance of class `CL_RSPO_PDF_MERGER`. To create this instance, class `CL_RSPO_PDF_MERGER` provides the method `CREATE_INSTANCE`. After using this method, the following two steps are necessary:

-   With method `ADD_DOCUMENT` you can add the data of a PDF document to the list of files you want to merge. You should call this method for each source file.

-   With method `MERGE_DOCUMENTS` you can start the merge process. The method returns the data of the merged document.


> ### Sample Code:  
> ```abap
> ...   
>     " Create an instance of the PDF merger class
>     DATA(l_merger) = cl_rspo_pdf_merger=>create_instance( ).
> 
>     " Add the data of the first PDF document to the list of files which shall be merged
>     l_merger->add_document( l_data_of_first_pdf ).
>     " Add the data of the second PDF document
>     l_merger->add_document( l_data_of_second_pdf ).
> 
>     TRY.
>         " Merge both documents and receive the result
>           DATA(l_merged_PDF) = l_merger->merge_documents( ).
>       CATCH cx_rspo_pdf_merger INTO DATA(l_exception).
>         " Add a useful error handling here
>     ENDTRY.
> ...
> ```

If you try to merge damaged documents, or documents that don't fulfill the requirements of the PDF merger, an exception of type `CX_RSPO_PDF_MERGER` is raised. The exception object contains the following attributes that contain more information regarding the problem:

-   `DOCUMENT_INDEX`: The index of the PDF document that was responsible for the exception
-   `ERROR_CODE`: The internal error code of the exception
-   `ERROR_TEXT`: The description text of the error code

The PDF merger has the following restrictions:

-   It can only handle PDF files.
-   It can't handle encrypted PDF files. Usually, you can check whether a PDF file is encrypted by checking the *Security* section of the file properties. Another possibility is that you open the file with a text editor and search for the key word **Encrypt**, which marks an encrypted file.
-   It can't handle damaged PDF files. For example, if parts of the file are missing, or if some bytes were changed, the file can't be processed. PDF files are usually binary data, so any conversion like a code page conversion damages the file.
-   Further restrictions can be found in SAP note [2264208](https://me.sap.com/notes/2264208).

**Related Information**  


[Class and Interface of the PDF Merger API](class-and-interface-of-the-pdf-merger-api-f647ef4.md "Class CL_RSPO_PDF_MERGER uses interface IF_RSPO_PDF_MERGER. Find out which public methods it contains.")

