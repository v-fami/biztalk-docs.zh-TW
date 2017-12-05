---
title: "正在驗證配接器組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8eeb8742-7083-462b-8d3a-e58103112542
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c03054332e0cd2117c1219afec3dd1aa0a09d6bd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="validating-the-adapter-configuration"></a><span data-ttu-id="3a437-102">驗證配接器組態</span><span class="sxs-lookup"><span data-stu-id="3a437-102">Validating the Adapter Configuration</span></span>
<span data-ttu-id="3a437-103">同時新增接收位置和傳送埠，您必須設定您的自訂屬性中 **\<** *配接器名稱* **\>傳輸屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3a437-103">While adding the receive location and send port, you will be asked to configure your custom properties in the **\<***Adapter Name***\> Transport Properties** dialog box.</span></span> <span data-ttu-id="3a437-104">AdapterHarness 專案中的 XSD 結構描述檔案會定義這些屬性。</span><span class="sxs-lookup"><span data-stu-id="3a437-104">The XSD schema files in the AdapterHarness project define these properties.</span></span>  
  
 <span data-ttu-id="3a437-105">組態結構描述的驗證發生在以下三個部分中：</span><span class="sxs-lookup"><span data-stu-id="3a437-105">Validation of the configuration schema occurs in three parts:</span></span>  
  
1.  <span data-ttu-id="3a437-106">當顯示儲存的組態時，配接器架構會先針對此結構描述來驗證儲存的 XML 文件，然後此文件才會載入到屬性頁。</span><span class="sxs-lookup"><span data-stu-id="3a437-106">When displaying a saved configuration, the Adapter Framework validates the saved XML document against the schema before loading the document into the property page.</span></span> <span data-ttu-id="3a437-107">此架構假設非有效的文件表示組態結構描述定義中有變更。</span><span class="sxs-lookup"><span data-stu-id="3a437-107">The framework assumes that a document that is not valid indicates a change in the configuration schema definition.</span></span> <span data-ttu-id="3a437-108">只有有效的文件才會載入到屬性頁。</span><span class="sxs-lookup"><span data-stu-id="3a437-108">Only valid documents get loaded into the property page.</span></span>  
  
2.  <span data-ttu-id="3a437-109">當儲存組態時，如果配接器實作**IAdapterConfigValidation**介面，架構會傳遞至建構的 XML 文件的配接器從序列化屬性頁資料。</span><span class="sxs-lookup"><span data-stu-id="3a437-109">When saving a configuration, if the adapter implements the **IAdapterConfigValidation** interface, the framework passes to the adapter the XML document constructed from serializing the property page data.</span></span> <span data-ttu-id="3a437-110">然後，此配接器會處理該文件。</span><span class="sxs-lookup"><span data-stu-id="3a437-110">The adapter then processes the document.</span></span> <span data-ttu-id="3a437-111">任何錯誤都應該會產生此架構所攔截並顯示給使用者的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3a437-111">Any errors should produce exceptions that are caught by the framework and displayed to the user.</span></span> <span data-ttu-id="3a437-112">任何遺漏或產生的值都應該在驗證期間產生。</span><span class="sxs-lookup"><span data-stu-id="3a437-112">Any missing or generated values should be generated during validation.</span></span> <span data-ttu-id="3a437-113">使用\<可瀏覽顯示 ="false"\>裝飾會隱藏項目顯示在屬性方格中，即使值出現在 XML 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a437-113">Using the \<browsable show="false"\> decoration suppresses showing an entry in the property grid, even though the value appears in the XML instance.</span></span>  
  
3.  <span data-ttu-id="3a437-114">將該值放到資料庫之前儲存組態時，此架構會再次針對此結構描述來驗證此 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="3a437-114">When saving a configuration before placing the value into the database, the framework again validates the XML document against the schema.</span></span> <span data-ttu-id="3a437-115">如此可確保只會保存有效的資料。</span><span class="sxs-lookup"><span data-stu-id="3a437-115">This ensures that only valid data is persisted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a437-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a437-116">See Also</span></span>  
 [<span data-ttu-id="3a437-117">配接器設計問題</span><span class="sxs-lookup"><span data-stu-id="3a437-117">Adapter Design Issues</span></span>](../core/adapter-design-issues.md)