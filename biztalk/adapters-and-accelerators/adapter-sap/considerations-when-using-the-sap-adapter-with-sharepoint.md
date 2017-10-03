---
title: "與 SharePoint 中使用 SAP 配接器時的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d310741-b648-4028-a75f-35b843edcc8d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07aef41626c9ac2336565cdca9fa3470bf0144e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-using-the-sap-adapter-with-sharepoint"></a>與 SharePoint 中使用 SAP 配接器時的考量
本主題包含使用時可能會遇到問題的相關資訊[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]與 Microsoft Office SharePoint Server，以及解決方式。 問題分為兩類：  
  
-   一般問題  
  
-   包含自訂 Web 組件的問題  
  
## <a name="general-issues"></a>一般問題  
 本節中的問題有解決方案，或需要您修改應用程式定義檔的解析度。  
  
### <a name="issue-1-the-simple-type-data-returned-by-the-wcf-service-is-not-displayed"></a>問題 1： 不顯示 WCF 服務所傳回的簡單型別資料  
 **說明**: Microsoft Office SharePoint Server 預期的資料集或集合類型的 WCF 服務所傳回的資料。 Microsoft Office SharePoint Server 的 WCF 服務所傳回的資料是簡單類型，不會顯示資料。  
  
 **解析**： 沒有解決方式。 它是 Microsoft Office SharePoint Server 的已知的限制。  
  
### <a name="issue-2-an-error-message-is-displayed-if-the-data-returned-by-the-wcf-service-is-null"></a>問題 2： 錯誤訊息會顯示如果 WCF 服務所傳回的資料為 NULL  
 **說明**: Microsoft Office SharePoint Server 的 WCF 服務所傳回的資料是否為 NULL 值，顯示錯誤訊息。 例如，假設您使用商務資料清單網頁組件，如**Finder**方法執行個體，並搜尋搜尋運算式為基礎之 SAP 系統內的客戶。 您指定的搜尋運算式會擷取 NULL 值。 在此情況下，Microsoft Office SharePoint Server 將會顯示錯誤訊息。  
  
 **解析**： 沒有解決方式。 它是 Microsoft Office SharePoint Server 的已知的限制。  
  
### <a name="issue-3-an-array-of-simple-type-returned-by-the-wcf-service-is-not-displayed"></a>問題 3： 不顯示 WCF 服務所傳回的簡單類型的陣列  
 **說明**: WCF 服務所傳回的資料是簡單類型的陣列，如果 Microsoft Office SharePoint Server 不會顯示資料。 此外，當您執行的方法執行個體中商務資料目錄定義編輯器傳回簡單類型的陣列，會顯示下列錯誤訊息: 「 後端系統的配接器傳回的結構與對應的中繼資料 （不相容MethodInstance、 參數或 TypeDescriptor）。 」  
  
 **解析**： 沒有解決方式。 它是與 Microsoft Office SharePoint Server 和商務資料目錄定義編輯器的已知的限制。  
  
### <a name="issue-4-cannot-import-an-application-definition-file-that-contains-a-complex-type-parameter-having-more-than-300-fields"></a>問題 4： 無法匯入應用程式定義檔包含具有超過 300 個欄位的複雜型別參數  
 **說明**: Microsoft Office SharePoint Server 無法匯入具有超過 300 個 WCF 服務所傳回的複雜型別參數中的欄位，並顯示錯誤訊息，如果您嘗試執行這項操作的應用程式定義檔。 這是因為 Microsoft Office SharePoint Server 無法顯示超過 300 個欄位的複雜型別參數的限制。  
  
 **解析**： 使用商務資料目錄定義編輯器的小於或等於 300 的複雜型別參數的欄位數目限制。 根據您的需求，您可以刪除複雜型別參數中商務資料目錄定義編輯器，您不需要在 Microsoft Office SharePoint Server 中顯示的欄位。  或者，您可以在此也匯出從商務資料目錄定義編輯器的應用程式定義檔與所有的欄位，然後再修改應用程式定義檔，在記事本或任何 XML 撰寫的應用程式刪除未使用的欄位才能限制為 300 的欄位數目。  
  
##  <a name="Custom_Web_Part"></a>包含自訂 Web 組件的問題  
 本章節包含的解決方法都需要使用自訂 Web 組件的問題。 如需使用自訂的 Web 組件來解決使用時可能出現的問題詳細資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和 Microsoft Office SharePoint Server，請參閱[SAP 配接器搭配使用自訂的 Web 組件](../../adapters-and-accelerators/adapter-sap/use-a-custom-web-part-with-the-sap-adapter.md)。  
  
###  <a name="Issue1"></a>問題 1： 與 Microsoft Office SharePoint Server 中顯示單一記錄限制根據多個值  
 **說明**： 如果您想要顯示單一記錄根據 SAP 系統中的多個值 （輸入參數） 的 Microsoft Office SharePoint Server 中，您無法使用任何三個 Web 組件 （商務資料清單、 商務資料的項目和 Business資料相關的清單） 中指定[步驟 3： 建立 SharePoint 應用程式以擷取資料從 SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)中[教學課程 1： 從 SharePoint 網站上的 SAP 系統的呈現資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)。  
  
 **解析**： 您必須使用自訂的 Web 組件來執行這項操作。 使用自訂的 Web 組件的相關資訊，請參閱[SAP 配接器搭配使用自訂的 Web 組件](../../adapters-and-accelerators/adapter-sap/use-a-custom-web-part-with-the-sap-adapter.md)。 在 「 步驟 1:: 建立自訂 Web 組件 」 該主題的您可以使用在步驟 5 中的下列程式碼範例。 下列程式碼範例採用 BankCountry 和 BankKey 做為輸入參數，並再將其顯示為 Microsoft Office SharePoint Server 中的單一記錄。  
  
```  
namespace CustomWebPart  
{  
    public class CustomWebPart : WebPart  
    {  
        private string displayText = "Hello World!";  
  
        [WebBrowsable(true), Personalizable(true)]  
        public string DisplayText  
        {  
            get { return displayText; }  
            set { displayText = value; }  
        }  
        protected override void Render(System.Web.UI.HtmlTextWriter writer)  
        {  
            string BankCountry = "US";  
            string BankKey = "134329042";  
  
/***Step 1: Get the required entity and method.***/  
  
            LobSystem newSystem = ApplicationRegistry.GetLobSystems()["BAPI_BANK_GETDETAIL"]; // Name specified in application definition file  
            LobSystemInstance newSystemInstance = newSystem.GetLobSystemInstances()["BAPI_BANK_GETDETAIL_Instance"]; // Name specified in application definition file  
            Entity CategoryEntity = newSystem.GetEntities()["Entity"]; // Name specified in application definition file  
            Method newMethod = CategoryEntity.GetMethods()["BAPI_BANK_GETDETAIL"]; // Name specified in application definition file  
            MethodInstance methodInstance = newMethod.GetMethodInstances()["MethodInstance"]; // Name specified in application definition file  
  
/***Step 2: Get the list of input parameters.***/  
  
            Object[] args = methodInstance.GetMethod().CreateDefaultParameterInstances(methodInstance); //Get the default values of the input parameters.  
            Object[] ArgsInput = new Object[args.Length];  
  
/***Step 3: Assign them required values.***/  
  
            Type t = null;  
            char[] myString = BankCountry.ToCharArray();  
            String s = new String(myString);  
            t = s.GetType();  
            ArgsInput[0] = Activator.CreateInstance(t, myString);  
  
            myString = BankKey.ToCharArray();  
            s = new String(myString);  
            t = s.GetType();  
            ArgsInput[1] = Activator.CreateInstance(t, myString);  
  
/***Step 4: Execute the particular method instance using the required value.***/  
  
            IEntityInstance IE = (IEntityInstance)CategoryEntity.Execute(methodInstance, newSystemInstance, ref ArgsInput); //Method instance of type Specific Finder is being used here.  
  
/***Step 5: Display the output on the custom Web Part in Microsoft Office SharePoint Server.***/  
  
            writer.Write("<table>");  
            writer.Write("<tr>");  
            foreach (Field f in CategoryEntity.GetFinderView().Fields)  
            {  
                writer.Write("<td>");  
                writer.Write(IE[f]);  
                writer.Write("</td>");  
            }  
            writer.Write("</tr>");  
            writer.Write("</table>");  
        }  
    }  
  
```  
  
> [!NOTE]
>  應用程式定義檔必須包含**特定搜尋工具**方法執行個體。 A**特定搜尋工具**方法會尋找特定的記錄識別碼為基礎。 如需建立資訊**特定搜尋工具**方法執行個體，請參閱中的 「 需求 2:: 擷取詳細資料的特定客戶從清單中的客戶 」[步驟 2： 建立適用於 SAP 的應用程式定義檔成品](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)中[教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)。  
  
### <a name="issue-2-cannot-specify-values-to-array-elements"></a>問題 2： 無法指定陣列元素的值  
 **說明**: WCF 服務的輸入的參數是陣列，如果您不能指定使用在建立使用商務資料目錄定義編輯器的應用程式定義檔案中定義的篩選條件的陣列元素的值。 這表示，您無法使用的商務資料清單或商務資料的項目 Web 組件中 Microsoft Office SharePoint Server 來指定這些輸入參數 （陣列的項目） 的 WCF 服務的值。 這是因為應用程式定義檔中定義陣列的方式。  
  
 **解析**： 將值指派給陣列項目使用自訂的 Web 組件。 使用自訂的 Web 組件的相關資訊，請參閱[SAP 配接器搭配使用自訂的 Web 組件](../../adapters-and-accelerators/adapter-sap/use-a-custom-web-part-with-the-sap-adapter.md)。 例如，您可以使用下列程式碼範例中的步驟 3 中 「 問題 1： 與 Microsoft Office SharePoint Server 中顯示單一記錄限制根據多個值 」 將值指派給陣列項目。  
  
```  
/***Assign required values to parameters of type array.***/   
/***Assumption is that the ith parameter of Method is of type Array and all the simple type elements in the array are of string type.***/  
  
            Type t = asm.GetType(args[i].GetType().ToString()); // Get type of the parameter  
            Type TElement = t.GetElementType(); // Getting type of element of array  
            int index = 5; //Size of Array  
            Array ElementArray = Array.CreateInstance(TElement, index); //Creating an array of length: index  
  
            for (int ind = 0; ind < index; ind++)  
            {  
                //Creating an instance of an element of array  
                object ElementType = Activator.CreateInstance(TElement);  
                FieldInfo[] FI = ElementType.GetType().GetFields();  
                for (int f = 0; f \< FI.Length; f++)  
                {  
                    ElementType.GetType().GetFields()[f].SetValue(ElementType, (Object)"ElementValue");  
                }  
                ElementArray.SetValue(ElementType, ind);  
            }  
  
            ArgsInput[i] = (object)ElementArray; // As shown in sample, ArgsInput is fed as input while executing Method Instance  
  
```  
  
### <a name="issue-3-limitation-with-specifying-null-values-to-complex-type-parameters"></a>問題 3： 限制指定 NULL 值的複雜型別參數  
 **說明**： 如果您不指定 Microsoft Office SharePoint Server 中的複雜型別參數從 Web 組件的任何值，NULL 應該傳遞做為複雜型別參數的值至 WCF 服務。 不過，非 NULL 值會傳遞針對複雜型別參數，並會將 NULL 傳遞其 （屬於簡單類型） 的子系元素。 這會導致預期的訊息結構描述與傳遞至 WCF 服務的訊息結構描述不符。 如此一來，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可能會顯示錯誤訊息。  
  
> [!NOTE]
>  若要瞭解複雜型別參數的預設值，從 Microsoft Office SharePoint Server 中的 Web 組件沒有傳遞任何值時，使用步驟 2 中的程式碼範例中所述"問題 1： 在 Microsoft Office SharePoint Server 中顯示單一記錄與限制根據多個值。 」  
  
 **解析**： 使用自訂的 Web 組件將 NULL 值指派給複雜型別參數。 使用自訂的 Web 組件的相關資訊，請參閱[SAP 配接器搭配使用自訂的 Web 組件](../../adapters-and-accelerators/adapter-sap/use-a-custom-web-part-with-the-sap-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[搭配 SharePoint 使用 SAP 配接器](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md)