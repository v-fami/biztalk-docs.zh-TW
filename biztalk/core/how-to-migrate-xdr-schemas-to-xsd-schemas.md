---
title: "如何將 XDR 結構描述移轉至 XSD 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bde0d0-bfe6-4d6c-823c-8ed9c0e15783
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84bbc42297a10c7d42adb8d778ba19b3b392742c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-migrate-xdr-schemas-to-xsd-schemas"></a><span data-ttu-id="842ea-102">如何將 XDR 結構描述移轉至 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="842ea-102">How to Migrate XDR Schemas to XSD Schemas</span></span>
<span data-ttu-id="842ea-103">若您正在移轉舊版 BizTalk Server 的結構描述，您需要將 XML-Data Reduced (XDR) 結構描述轉換為 XML 結構描述定義 (XSD) 語言結構描述。</span><span class="sxs-lookup"><span data-stu-id="842ea-103">If you are migrating schemas from a previous version of BizTalk Server, you will need to convert your XML-Data Reduced (XDR) schemas into XML Schema definition (XSD) language schemas.</span></span> <span data-ttu-id="842ea-104">本主題描述必要的步驟。</span><span class="sxs-lookup"><span data-stu-id="842ea-104">This topic describes the necessary steps.</span></span>  
  
### <a name="to-generate-an-xsd-schema-from-an-xdr-schema"></a><span data-ttu-id="842ea-105">從 XDR 結構描述產生 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="842ea-105">To generate an XSD schema from an XDR schema</span></span>  
  
1.  <span data-ttu-id="842ea-106">在**方案總管] 中**，以滑鼠右鍵按一下相關的 BizTalk 專案，指向**新增**，然後按一下 [**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="842ea-106">In **Solution Explorer**, right-click the relevant BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="842ea-107">在**加入產生的項目- \<* BizTalk ProjectName*\>* * 對話方塊中，於**範本**區段中，按一下**產生結構描述**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="842ea-107">In the **Add Generated Item - \<*BizTalk ProjectName*\>** dialog box, in the **Templates** section, click **Generate Schemas**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="842ea-108">在**產生結構描述**對話方塊中，於**文件類型**清單中，選取**XDR 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="842ea-108">In the **Generate Schemas** dialog box, in the **Document type** list, select **XDR Schema**.</span></span>  
  
4.  <span data-ttu-id="842ea-109">按一下**瀏覽**，找出您想要移轉，然後按一下 XDR 結構描述檔案**確定**。</span><span class="sxs-lookup"><span data-stu-id="842ea-109">Click **Browse**, locate the XDR schema file you want to migrate, and then click **OK**.</span></span>  
  
     <span data-ttu-id="842ea-110">會從指定的 XDR 結構描述檔案產生新的結構描述，使用副檔名為 .xsd 的檔案之相同名稱，然後在 [BizTalk 編輯器] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="842ea-110">A new schema is generated from the specified XDR schema file, using the same name as that file with the .xsd extension, and then opened in BizTalk Editor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="842ea-111">避免使用 C# 保留字與 .NET Framework 類型和命名空間名稱 (如 System) 做為結構描述根節點名稱或檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="842ea-111">Avoid using C# reserved words and .NET Framework type and namespace names (such as System) as schema root node names or as file names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842ea-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="842ea-112">See Also</span></span>  
 <span data-ttu-id="842ea-113">[管理專案中的結構描述](../core/managing-schemas-within-projects.md) </span><span class="sxs-lookup"><span data-stu-id="842ea-113">[Managing Schemas Within Projects](../core/managing-schemas-within-projects.md) </span></span>  
 [<span data-ttu-id="842ea-114">移轉一般檔案記錄</span><span class="sxs-lookup"><span data-stu-id="842ea-114">Migrating Flat File Records</span></span>](../core/migrating-flat-file-records.md)