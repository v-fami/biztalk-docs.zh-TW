---
title: "從 XML 檔案匯入協議屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8bf5268-1742-47da-b42f-6472706a9bff
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3ac08628931ec4111eb1b5a9ad86991344c22d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-agreement-properties-from-an-xml-file"></a><span data-ttu-id="3e140-102">從 XML 檔案匯入協議屬性</span><span class="sxs-lookup"><span data-stu-id="3e140-102">Importing Agreement Properties from an XML File</span></span>
<span data-ttu-id="3e140-103">本節提供如何從 XML 範本檔案匯入協議屬性的指示。</span><span class="sxs-lookup"><span data-stu-id="3e140-103">This section provides instructions on how to import agreement properties from an XML template file.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3e140-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="3e140-104">Prerequisites</span></span>  
 <span data-ttu-id="3e140-105">以下是執行此主題中之程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="3e140-105">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="3e140-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="3e140-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
-   <span data-ttu-id="3e140-107">您必須匯出協議至 XML 範本檔案中所述[將協議屬性匯出至 XML 檔案](../core/exporting-agreement-properties-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="3e140-107">You must have exported an agreement to an XML template file, as described in [Exporting Agreement Properties to an XML FIle](../core/exporting-agreement-properties-to-an-xml-file.md).</span></span>  
  
### <a name="to-import-agreement-properties-from-an-xml-file"></a><span data-ttu-id="3e140-108">若要從 XML 檔案匯入協議屬性</span><span class="sxs-lookup"><span data-stu-id="3e140-108">To import agreement properties from an XML file</span></span>  
  
1.  <span data-ttu-id="3e140-109">在[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]管理主控台中，按一下 **合作對象**節點下的**BizTalk Server 管理**和**BizTalk 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="3e140-109">In the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration Console, click the **Parties** node under the **BizTalk Server Administration** and **BizTalk Group** nodes.</span></span> <span data-ttu-id="3e140-110">在**合作對象與商務設定檔**頁面上，依照建立協議[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="3e140-110">In the **Parties and Business Profiles** page, create an agreement as described at [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span>  
  
2.  <span data-ttu-id="3e140-111">在**協議屬性**對話方塊中，按一下 **從範本載入**。</span><span class="sxs-lookup"><span data-stu-id="3e140-111">In the **Agreement Properties** dialog box, click **Load From Template**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e140-112">**從範本載入**選取協議的通訊協定之後，才會啟用按鈕。</span><span class="sxs-lookup"><span data-stu-id="3e140-112">The **Load From Template** button is enabled only after you select a protocol for the agreement.</span></span> <span data-ttu-id="3e140-113">當您指定通訊協定時，您也同時隱含地宣告了您只能為匯入相同編碼通訊協定的協議。</span><span class="sxs-lookup"><span data-stu-id="3e140-113">When you specify the protocol you also implicitly declare that you can only import an agreement for the same encoding protocol.</span></span>  
  
3.  <span data-ttu-id="3e140-114">在**開啟**對話方塊中，瀏覽至 XML 範本檔案的位置選取檔案，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="3e140-114">In the **Open** dialog box, browse to the location of the XML template file, select the file, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="3e140-115">在**建立範本**方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3e140-115">In the **Create Template** box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e140-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e140-116">See Also</span></span>  
 <span data-ttu-id="3e140-117">[重複使用另一個協議屬性](../core/reusing-properties-from-another-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="3e140-117">[Reusing Properties from Another Agreement](../core/reusing-properties-from-another-agreement.md) </span></span>  
 [<span data-ttu-id="3e140-118">將協議屬性匯出至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="3e140-118">Exporting Agreement Properties to an XML FIle</span></span>](../core/exporting-agreement-properties-to-an-xml-file.md)