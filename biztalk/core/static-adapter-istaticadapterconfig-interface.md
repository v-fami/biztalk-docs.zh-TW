---
title: "靜態配接器 IStaticAdapterConfig 介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f5de01-0cfc-456a-a52b-28f8f076bdfc
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de8d95ba4a5945cb43e3681055750cdad628759
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="static-adapter-istaticadapterconfig-interface"></a><span data-ttu-id="bd6bf-102">靜態配接器 IStaticAdapterConfig 介面</span><span class="sxs-lookup"><span data-stu-id="bd6bf-102">Static Adapter IStaticAdapterConfig Interface</span></span>
<span data-ttu-id="bd6bf-103">靜態設計階段配接器必須實作**IStaticAdapterConfig**介面。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-103">A static design-time adapter must implement the **IStaticAdapterConfig** interface.</span></span> <span data-ttu-id="bd6bf-104">這可讓它和「新增配接器中繼資料精靈」進行互動，並從配接器取得服務組織和個別的服務描述。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-104">This allows it to interact with the Add Adapter Metadata Wizard and obtain service organizations and individual service descriptions from the adapter.</span></span> <span data-ttu-id="bd6bf-105">此精靈會呼叫**GetServiceOrganization**和**GetServiceDescription**方法來提取與配接器互動的中繼資料資訊，並將它新增至 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-105">The wizard calls the **GetServiceOrganization** and **GetServiceDescription** methods to pull in metadata information with which the adapter interacts and add it to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd6bf-106">**GetServiceOrganization**方法會取得表示配接器的公開服務的階層式組織的 XML 執行個體文件。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-106">The **GetServiceOrganization** method obtains an XML instance document that represents the hierarchical organization of the adapter's exposed services.</span></span> <span data-ttu-id="bd6bf-107">此結構會產生服務組織樹狀結構上看到**選取要匯入服務**中新增配接器中繼資料精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-107">This structure generates the service organization tree that you see on the **Select Services to Import** page in the Add Adapter Metadata Wizard.</span></span>  
  
 <span data-ttu-id="bd6bf-108">選取要匯入服務之後，精靈就會呼叫**GetServiceDescription**方法，以取得對應到已在 新增選取的服務類別目錄 Web 服務描述語言 (WSDL) 檔案的陣列配接器中繼資料精靈 」 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-108">After you select the services to import, the wizard calls the **GetServiceDescription** method to obtain an array of Web Services Description Language (WSDL) files corresponding to the service categories that were selected in the Add Adapter Metadata Wizard tree.</span></span> <span data-ttu-id="bd6bf-109">表示服務的結構描述會產生為 XSD 檔案，並在您完成「新增配接器中繼資料精靈」後新增至您的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-109">Schemas representing the services are generated as XSD files and added to your BizTalk project after you complete the Add Adapter Metadata Wizard.</span></span>  
  
 <span data-ttu-id="bd6bf-110">在檔案配接器範例中， **GetServiceOrganization**和**GetServiceDescription**方法位於**StaticAdapterManagement**類別AdapterManagement.cs 類別檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-110">In the file adapter sample, the **GetServiceOrganization** and **GetServiceDescription** methods reside in the **StaticAdapterManagement** class in the AdapterManagement.cs class file.</span></span> <span data-ttu-id="bd6bf-111">此精靈會呼叫**GetServiceOrganization**方法，以取得上顯示的樹狀結構**選取要匯入服務**頁面。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-111">The wizard calls the **GetServiceOrganization** method to obtain the tree structure to display on the **Select Services to Import** page.</span></span> <span data-ttu-id="bd6bf-112">在**GetServicesOrganization**硬式編碼的 AdapterManagement.CategorySchema.xml 檔案會使用傳回值中的下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-112">In **GetServicesOrganization** the hard-coded return value of AdapterManagement.CategorySchema.xml file is used as shown in the following code fragment.</span></span> <span data-ttu-id="bd6bf-113">身為配接器開發人員，您必須加入此邏輯，以傳回適當的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-113">As an adapter developer you will need to add the logic to return the appropriate XML file.</span></span>  
  
```  
public string GetServiceOrganization(IPropertyBag endPointConfiguration, string NodeIdentifier)   
{  
   string result = GetResource("AdapterManagement.CategorySchema.xml");  
   return result;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="bd6bf-114">請務必修改**GetServiceDescription**方法**StaticAdapterManagement**類別，而不是**DynamicAdapterManagement**中第一個出現的類別檔案中。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-114">Be sure to modify the **GetServiceDescription** method of the **StaticAdapterManagement** class, and not of the **DynamicAdapterManagement** class, which appears first in the file.</span></span>  
  
 <span data-ttu-id="bd6bf-115">下列程式碼取自**GetServiceDescription** AdapterManagement.cs 檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-115">The following code is from the **GetServiceDescription** method of the AdapterManagement.cs file.</span></span> <span data-ttu-id="bd6bf-116">service1.wsdl 但會被硬式編碼為傳回的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-116">The file service1.wsdl is hard-coded as the WSDL file returned.</span></span> <span data-ttu-id="bd6bf-117">它會傳會表示為 WSDL 檔案的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-117">It returns schemas represented as WSDL files.</span></span> <span data-ttu-id="bd6bf-118">`wsdls`參數是對應至來源載入的 XML 中的 WSDL 參考的唯一 WSDL 參考的陣列**GetServicesOrganization**。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-118">The `wsdls` parameter is an array of unique WSDL references that correspond to the WSDL references in the source XML loaded by **GetServicesOrganization**.</span></span> <span data-ttu-id="bd6bf-119">WSDL 描述的傳回集用來產生 BizTalk 專案的連接埠類型和訊息類型。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-119">The returned set of WSDL descriptions are used to generate the port types and message types for the BizTalk project.</span></span> <span data-ttu-id="bd6bf-120">如果您在樹狀結構中有一個以上的結構描述類型可供選取，您將需要一個以上的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-120">If you have more than one schema type available for selection in the tree, you will need more than one WSDL file.</span></span> <span data-ttu-id="bd6bf-121">如果您有很多可能的結構描述和 WSDL 選擇，您可新增資料庫尋查來傳回正確的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6bf-121">If you have many possible schema and WSDL choices, you may want to add a database lookup to return the correct WSDL file.</span></span>  
  
```  
/// <summary>     
        /// Get the WSDL file name for the selected WSDL  
        /// </summary>  
        /// <param name="wsdls">place holder</param>  
        /// <returns>An empty string[]</returns>  
        public string[] GetServiceDescription(string[] wsdls)   
      {  
            string[] result = new string[1];  
            result[0] = GetResource("AdapterManagement.service1.wsdl");  
            return result;  
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd6bf-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd6bf-122">See Also</span></span>  
 [<span data-ttu-id="bd6bf-123">靜態設計階段配接器組態</span><span class="sxs-lookup"><span data-stu-id="bd6bf-123">Static Design-Time Adapter Configuration</span></span>](../core/static-design-time-adapter-configuration.md)