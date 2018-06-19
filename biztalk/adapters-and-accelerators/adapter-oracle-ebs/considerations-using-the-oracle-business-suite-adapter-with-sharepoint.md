---
title: 使用 Oracle Business Suite 介面卡和 SharePoint 的考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56de6267-ec34-4bd2-abd1-3f2b69876b36
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69f87b2971eeb9093257bc022ee12cdafed0dbf3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217510"
---
# <a name="considerations-using-the-oracle-business-suite-adapter-with-sharepoint"></a><span data-ttu-id="d3f6a-102">使用 Oracle Business Suite 介面卡和 SharePoint 的考量</span><span class="sxs-lookup"><span data-stu-id="d3f6a-102">Considerations using the Oracle-Business Suite adapter with SharePoint</span></span>
<span data-ttu-id="d3f6a-103">本主題包含使用時可能會遇到問題的相關資訊[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]與 Microsoft Office SharePoint Server，以及解決方式。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-103">This topic contains information about the issues you might encounter while using the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] with Microsoft Office SharePoint Server, along with resolutions.</span></span> <span data-ttu-id="d3f6a-104">問題分為兩類：</span><span class="sxs-lookup"><span data-stu-id="d3f6a-104">The issues are divided into two categories:</span></span>  
  
-   <span data-ttu-id="d3f6a-105">一般問題</span><span class="sxs-lookup"><span data-stu-id="d3f6a-105">General issues</span></span>  
  
-   <span data-ttu-id="d3f6a-106">包含自訂 Web 組件的問題</span><span class="sxs-lookup"><span data-stu-id="d3f6a-106">Issues involving custom Web Parts</span></span>  
  
## <a name="general-issues"></a><span data-ttu-id="d3f6a-107">一般問題</span><span class="sxs-lookup"><span data-stu-id="d3f6a-107">General Issues</span></span>  
 <span data-ttu-id="d3f6a-108">本章節包含在沒有解析的問題。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-108">This section contains issues that have no resolution.</span></span>  
  
### <a name="issue-1-the-simple-type-data-returned-by-the-wcf-service-is-not-displayed"></a><span data-ttu-id="d3f6a-109">問題 1： 不顯示 WCF 服務所傳回的簡單型別資料</span><span class="sxs-lookup"><span data-stu-id="d3f6a-109">Issue 1: The simple type data returned by the WCF service is not displayed</span></span>  
 <span data-ttu-id="d3f6a-110">**說明**: Microsoft Office SharePoint Server 預期的資料集或集合類型的 WCF 服務所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-110">**Explanation**: Microsoft Office SharePoint Server expects the data returned by the WCF service to be of DataSet or Collection type only.</span></span> <span data-ttu-id="d3f6a-111">Microsoft Office SharePoint Server 的 WCF 服務所傳回的資料是簡單類型，不會顯示資料。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-111">If the data returned by the WCF service is of simple type, Microsoft Office SharePoint Server does not display the data.</span></span>  
  
 <span data-ttu-id="d3f6a-112">**解析**： 沒有解決方式。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-112">**Resolution**: No resolution.</span></span> <span data-ttu-id="d3f6a-113">它是 Microsoft Office SharePoint Server 的已知的限制。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-113">It is a known limitation with Microsoft Office SharePoint Server.</span></span>  
  
### <a name="issue-2-an-error-message-is-displayed-if-the-data-returned-by-the-wcf-service-is-null"></a><span data-ttu-id="d3f6a-114">問題 2： 錯誤訊息會顯示如果 WCF 服務所傳回的資料為 NULL</span><span class="sxs-lookup"><span data-stu-id="d3f6a-114">Issue 2: An error message is displayed if the data returned by the WCF service is NULL</span></span>  
 <span data-ttu-id="d3f6a-115">**說明**: Microsoft Office SharePoint Server 的 WCF 服務所傳回的資料是否為 NULL 值，顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-115">**Explanation**: If the data returned by the WCF service is a NULL value, Microsoft Office SharePoint Server displays an error message.</span></span> <span data-ttu-id="d3f6a-116">例如，假設您使用商務資料清單網頁組件，如**Finder**方法執行個體，並搜尋 Oracle E-business Suite 中的客戶會根據搜尋運算式。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-116">For example, suppose you are using the Business Data List Web Part for the **Finder** method instance, and are searching for customers in Oracle E-Business Suite based on a search expression.</span></span> <span data-ttu-id="d3f6a-117">您指定的搜尋運算式會擷取 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-117">The search expression that you specified fetches a NULL value.</span></span> <span data-ttu-id="d3f6a-118">在此情況下，Microsoft Office SharePoint Server 將會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-118">In this case, Microsoft Office SharePoint Server will display an error message.</span></span>  
  
 <span data-ttu-id="d3f6a-119">**解析**： 沒有解決方式。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-119">**Resolution**: No resolution.</span></span> <span data-ttu-id="d3f6a-120">它是 Microsoft Office SharePoint Server 的已知的限制。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-120">It is a known limitation with Microsoft Office SharePoint Server.</span></span>  
  
### <a name="issue-3-an-array-of-simple-type-returned-by-the-wcf-service-is-not-displayed"></a><span data-ttu-id="d3f6a-121">問題 3： 不顯示 WCF 服務所傳回的簡單類型的陣列</span><span class="sxs-lookup"><span data-stu-id="d3f6a-121">Issue 3: An array of simple type returned by the WCF service is not displayed</span></span>  
 <span data-ttu-id="d3f6a-122">**說明**: WCF 服務所傳回的資料是簡單類型的陣列，如果 Microsoft Office SharePoint Server 不會顯示資料。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-122">**Explanation**: If the data returned by the WCF service is an array of simple type, Microsoft Office SharePoint Server does not display the data.</span></span> <span data-ttu-id="d3f6a-123">此外，當您執行的方法執行個體中商務資料目錄定義編輯器傳回簡單類型的陣列，會顯示下列錯誤訊息: 「 後端系統的配接器傳回的結構與對應的中繼資料 （不相容MethodInstance、 參數或 TypeDescriptor）。 」</span><span class="sxs-lookup"><span data-stu-id="d3f6a-123">Moreover, when you execute a method instance in Business Data Catalog Definition Editor that returns an array of simple type, the following error message is displayed: “Backend system adapter returned a structure incompatible with the corresponding metadata (MethodInstance, Parameter or TypeDescriptor).”</span></span>  
  
 <span data-ttu-id="d3f6a-124">**解析**： 沒有解決方式。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-124">**Resolution**: No resolution.</span></span> <span data-ttu-id="d3f6a-125">它是與 Microsoft Office SharePoint Server 和商務資料目錄定義編輯器的已知的限制。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-125">It is a known limitation with Microsoft Office SharePoint Server and Business Data Catalog Definition Editor.</span></span>  
  
### <a name="issue-4-cannot-import-an-application-definition-file-that-contains-a-complex-type-parameter-having-more-than-300-fields"></a><span data-ttu-id="d3f6a-126">問題 4： 無法匯入應用程式定義檔包含具有超過 300 個欄位的複雜型別參數</span><span class="sxs-lookup"><span data-stu-id="d3f6a-126">Issue 4: Cannot import an application definition file that contains a complex type parameter having more than 300 fields</span></span>  
 <span data-ttu-id="d3f6a-127">**說明**: Microsoft Office SharePoint Server 無法匯入具有超過 300 個 WCF 服務所傳回的複雜型別參數中的欄位，並顯示錯誤訊息，如果您嘗試執行這項操作的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-127">**Explanation**: Microsoft Office SharePoint Server cannot import an application definition file that has more than 300 fields in the complex type parameter returned by the WCF service, and displays an error message if you try to do so.</span></span> <span data-ttu-id="d3f6a-128">這是因為 Microsoft Office SharePoint Server 無法顯示超過 300 個欄位的複雜型別參數的限制。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-128">This is due to the limitation of Microsoft Office SharePoint Server of not being able to display more than 300 fields of a complex type parameter.</span></span>  
  
 <span data-ttu-id="d3f6a-129">**解析**： 使用商務資料目錄定義編輯器的小於或等於 300 的複雜型別參數的欄位數目限制。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-129">**Resolution**: Use the Business Data Catalog Definition Editor to limit the number of fields of the complex type parameter to less than or equal to 300.</span></span> <span data-ttu-id="d3f6a-130">根據您的需求，您可以刪除複雜型別參數中商務資料目錄定義編輯器，您不需要在 Microsoft Office SharePoint Server 中顯示的欄位。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-130">Depending on your requirement, you can delete the fields of the complex type parameter in the Business Data Catalog Definition Editor that you do not require to be displayed in Microsoft Office SharePoint Server.</span></span>  <span data-ttu-id="d3f6a-131">或者，您可以在此也匯出從商務資料目錄定義編輯器的應用程式定義檔與所有的欄位，然後再修改應用程式定義檔，在記事本或任何 XML 撰寫的應用程式刪除未使用的欄位才能限制為 300 的欄位數目。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-131">Alternatively, you can also export the application definition file from Business Data Catalog Definition Editor with all the fields, and then modify the application definition file in a notepad or any XML authoring application to delete the fields that are not required in order to limit the number of fields to 300.</span></span>  
  
##  <a name="Custom_Web_Part"></a><span data-ttu-id="d3f6a-132">包含自訂 Web 組件的問題</span><span class="sxs-lookup"><span data-stu-id="d3f6a-132">Issues Involving Custom Web Parts</span></span>  
 <span data-ttu-id="d3f6a-133">本章節包含的解決方法都需要使用自訂 Web 組件的問題。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-133">This section contains issues that require the use of custom Web Part for a resolution.</span></span> <span data-ttu-id="d3f6a-134">如需使用自訂的 Web 組件來解決使用時可能出現的問題詳細資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]和 Microsoft Office SharePoint Server，請參閱[如何自訂 web 組件使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-134">For detailed information about using a custom Web Part to resolve issues that might come up while working with [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and Microsoft Office SharePoint Server, see [How to use a custom web part with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span></span>  
  
###  <a name="Issue1"></a><span data-ttu-id="d3f6a-135">問題 1： 與 Microsoft Office SharePoint Server 中顯示單一記錄限制根據多個值</span><span class="sxs-lookup"><span data-stu-id="d3f6a-135">Issue 1: Limitation with displaying a single record in Microsoft Office SharePoint Server based on multiple values</span></span>  
 <span data-ttu-id="d3f6a-136">**說明**： 如果您想要顯示單一記錄根據 Oracle E-business Suite 中的多個值 （輸入參數） 的 Microsoft Office SharePoint Server 中，您無法使用任何三個 Web 組件 (商務資料清單、 商務資料的項目，並步驟 3 中指定的商務資料相關的清單）： 建立 SharePoint 應用程式以擷取資料從 Oracle E-business Suite 中[教學課程： 呈現資料，從 SharePoint 網站上的 Oracle E-business Suite](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-136">**Explanation**: If you want to display a single record in Microsoft Office SharePoint Server based on multiple values (input parameters) from Oracle E-Business Suite, you cannot use any of the three Web Parts (Business Data List, Business Data Item, and Business Data Related List) specified in Step 3: Create a SharePoint Application to Retrieve Data from Oracle E-Business Suite in [Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).</span></span>  
  
 <span data-ttu-id="d3f6a-137">**解析**： 您必須使用自訂的 Web 組件來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-137">**Resolution**: You must use a custom Web Part to do this.</span></span> <span data-ttu-id="d3f6a-138">使用自訂的 Web 組件的相關資訊，請參閱[如何自訂 web 組件使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-138">For information about using a custom Web Part, see [How to use a custom web part with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span></span> <span data-ttu-id="d3f6a-139">在 「 步驟 1:: 建立自訂 Web 組件 」 該主題的您可以使用在步驟 5 中的下列程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-139">In “Step 1: Create a Custom Web Part” of that topic, you can use the following code sample in step 5.</span></span> <span data-ttu-id="d3f6a-140">下列程式碼範例採用 BankCountry 和 BankKey 做為輸入參數，並再將其顯示為 Microsoft Office SharePoint Server 中的單一記錄。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-140">The following code sample takes BankCountry and BankKey as the input parameters, and then displays them as a single record in Microsoft Office SharePoint Server.</span></span>  
  
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
>  <span data-ttu-id="d3f6a-141">應用程式定義檔必須包含**特定搜尋工具**方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-141">The application definition file must contain the **Specific Finder** method instance.</span></span> <span data-ttu-id="d3f6a-142">A**特定搜尋工具**方法會尋找特定的記錄識別碼為基礎。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-142">A **Specific Finder** method finds a specific record based on an identifier.</span></span> <span data-ttu-id="d3f6a-143">如需建立資訊**特定搜尋工具**方法執行個體，請參閱中的 「 需求 2:: 擷取詳細資料的特定客戶從清單中的客戶 」[步驟 2： 建立應用程式定義檔案Oracle E-business Suite 成品](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)中[教學課程： 呈現資料，從 SharePoint 網站上的 Oracle E-business Suite](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-143">For information about creating a **Specific Finder** method instance, see “Requirement 2: Retrieve Details for a Specific Customer from the List of Customers” in [Step 2: Create an application definition file for the Oracle E-Business Suite artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md) in [Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).</span></span>  
  
### <a name="issue-2-cannot-specify-values-to-array-elements"></a><span data-ttu-id="d3f6a-144">問題 2： 無法指定陣列元素的值</span><span class="sxs-lookup"><span data-stu-id="d3f6a-144">Issue 2: Cannot specify values to array elements</span></span>  
 <span data-ttu-id="d3f6a-145">**說明**: WCF 服務的輸入的參數是陣列，如果您不能指定使用在建立使用商務資料目錄定義編輯器的應用程式定義檔案中定義的篩選條件的陣列元素的值。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-145">**Explanation**: If the input parameter of the WCF service is an array, you cannot specify values to the array elements using filters that are defined in the application definition file created using the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="d3f6a-146">這表示，您無法使用的商務資料清單或商務資料的項目 Web 組件中 Microsoft Office SharePoint Server 來指定這些輸入參數 （陣列的項目） 的 WCF 服務的值。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-146">It implies that you cannot use the Business Data List or Business Data Item Web Part in Microsoft Office SharePoint Server to specify values for these input parameters (elements of array) to the WCF service.</span></span> <span data-ttu-id="d3f6a-147">這是因為應用程式定義檔中定義陣列的方式。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-147">This is because of the way arrays are defined in the application definition file.</span></span>  
  
 <span data-ttu-id="d3f6a-148">**解析**： 將值指派給陣列項目使用自訂的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-148">**Resolution**: Use a custom Web Part to assign values to array elements.</span></span> <span data-ttu-id="d3f6a-149">使用自訂的 Web 組件的相關資訊，請參閱[如何自訂 web 組件使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-149">For information about using a custom Web Part, see [How to use a custom web part with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span></span> <span data-ttu-id="d3f6a-150">例如，您可以使用下列程式碼範例中的步驟 3 中 「 問題 1： 與 Microsoft Office SharePoint Server 中顯示單一記錄限制根據多個值 」 將值指派給陣列項目。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-150">For example, you can use the following code sample in step 3 in “Issue 1: Limitation with displaying a single record in Microsoft Office SharePoint Server based on multiple values” to assign values to array elements.</span></span>  
  
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
  
### <a name="issue-3-limitation-with-specifying-null-values-to-complex-type-parameters"></a><span data-ttu-id="d3f6a-151">問題 3： 限制指定 NULL 值的複雜型別參數</span><span class="sxs-lookup"><span data-stu-id="d3f6a-151">Issue 3: Limitation with specifying NULL values to complex type parameters</span></span>  
 <span data-ttu-id="d3f6a-152">**說明**： 如果您不指定 Microsoft Office SharePoint Server 中的複雜型別參數從 Web 組件的任何值，NULL 應該傳遞做為複雜型別參數的值至 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-152">**Explanation**: If you do not specify any value for a complex type parameter from a Web Part in Microsoft Office SharePoint Server, NULL should be passed on as the value for the complex type parameter to the WCF service.</span></span> <span data-ttu-id="d3f6a-153">不過，非 NULL 值會傳遞針對複雜型別參數，並會將 NULL 傳遞其 （屬於簡單類型） 的子系元素。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-153">However, a non-NULL value is passed for the complex type parameter, and NULL is passed for its children elements (of simple type).</span></span> <span data-ttu-id="d3f6a-154">這會導致預期的訊息結構描述與傳遞至 WCF 服務的訊息結構描述不符。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-154">This causes a mismatch between the expected message schema and the message schema that is passed on to the WCF service.</span></span> <span data-ttu-id="d3f6a-155">如此一來，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可能會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-155">As a result, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] might display an error message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3f6a-156">若要瞭解複雜型別參數的預設值，從 Microsoft Office SharePoint Server 中的 Web 組件沒有傳遞任何值時，使用步驟 2 中的程式碼範例中所述"問題 1： 在 Microsoft Office SharePoint Server 中顯示單一記錄與限制根據多個值。 」</span><span class="sxs-lookup"><span data-stu-id="d3f6a-156">To find out the default value of a complex type parameter when no value is passed from a Web Part in Microsoft Office SharePoint Server, use step 2 in the code sample mentioned in “Issue 1: Limitation with displaying a single record in Microsoft Office SharePoint Server based on multiple values.”</span></span>  
  
 <span data-ttu-id="d3f6a-157">**解析**： 使用自訂的 Web 組件將 NULL 值指派給複雜型別參數。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-157">**Resolution**: Use a custom Web Part to assign a NULL value to the complex type parameter.</span></span> <span data-ttu-id="d3f6a-158">使用自訂的 Web 組件的相關資訊，請參閱[如何自訂 web 組件使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f6a-158">For information about using a custom Web Part, see [How to use a custom web part with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f6a-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3f6a-159">See Also</span></span>  
[<span data-ttu-id="d3f6a-160">搭配 SharePoint 使用 Oracle E-business Suite 介面卡</span><span class="sxs-lookup"><span data-stu-id="d3f6a-160">Use the Oracle E-Business Suite adapter with SharePoint</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md)