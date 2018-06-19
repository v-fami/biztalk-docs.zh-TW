---
title: 重複使用另一個協議屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8e1cc60-d581-43ca-aa70-1e0d6238497a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7db2118f372014a3e8f108c1ff2273bc5aad976
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007423"
---
# <a name="reusing-properties-from-another-agreement"></a><span data-ttu-id="0b19e-102">重複使用另一個協議屬性</span><span class="sxs-lookup"><span data-stu-id="0b19e-102">Reusing Properties from Another Agreement</span></span>
<span data-ttu-id="0b19e-103">您可以將屬性重複運用在不同的協議上。</span><span class="sxs-lookup"><span data-stu-id="0b19e-103">You can reuse properties between agreements.</span></span> <span data-ttu-id="0b19e-104">當新協議大部分或所有的屬性皆與現有協議的屬性相同時，這種做法可節省大量時間。</span><span class="sxs-lookup"><span data-stu-id="0b19e-104">This can save a significant amount of time when either most or all of the properties of a new agreement are the same as those of an existing agreement.</span></span> <span data-ttu-id="0b19e-105">[!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] BizTalk Server 中的使用者介面可讓您匯出成 XML 範本檔案的協議。</span><span class="sxs-lookup"><span data-stu-id="0b19e-105">The [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] user interface in BizTalk Server enables you to export an agreement into an XML template file.</span></span> <span data-ttu-id="0b19e-106">以後您只要匯入該 XML 範本，就能重複使用相同的協議屬性。</span><span class="sxs-lookup"><span data-stu-id="0b19e-106">You can then import the XML template to reuse the same agreement properties.</span></span>  
  
 <span data-ttu-id="0b19e-107">將協議匯出成 XML 範本會擷取到協議中大部分 (但非全部) 的屬性。</span><span class="sxs-lookup"><span data-stu-id="0b19e-107">Exporting the agreement to an XML template captures most, but not all, properties from the agreement.</span></span> <span data-ttu-id="0b19e-108">下列屬性將*不*匯出至 XML 範本檔案：</span><span class="sxs-lookup"><span data-stu-id="0b19e-108">The following properties will *not* be exported to the XML template file:</span></span>  
  
-   <span data-ttu-id="0b19e-109">中的所有屬性**一般屬性**頁面**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0b19e-109">All the properties from the **General Properties** page in the **General** tab.</span></span>  
  
-   <span data-ttu-id="0b19e-110">中的所有屬性**連絡人**頁面**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0b19e-110">All the properties from the **Contacts** page in the **General** tab.</span></span>  
  
-   <span data-ttu-id="0b19e-111">中的所有屬性**其他屬性**頁面**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0b19e-111">All the properties from the **Additional Properties** page in the **General** tab.</span></span>  
  
-   <span data-ttu-id="0b19e-112">識別項相關的設定，從**識別碼**頁面的單向協議索引標籤。它們是：</span><span class="sxs-lookup"><span data-stu-id="0b19e-112">Identifier-related settings from the **Identifiers** page in the one-way agreement tab. These are:</span></span>  
  
    -   <span data-ttu-id="0b19e-113">**對於 X12**: ISA5、 ISA6、 ISA7、 ISA8 及其他的協議解析程式設定</span><span class="sxs-lookup"><span data-stu-id="0b19e-113">**For X12**: ISA5, ISA6, ISA7, ISA8, and additional agreement resolver settings</span></span>  
  
    -   <span data-ttu-id="0b19e-114">**對於 EDIFACT**: UNB 2.1、 UNB 2.2、 UNB 3.1、 UNB 3.2 及其他的協議解析程式設定</span><span class="sxs-lookup"><span data-stu-id="0b19e-114">**For EDIFACT**: UNB 2.1, UNB 2.2, UNB 3.1, UNB 3.2, and additional agreement resolver settings</span></span>  
  
    -   <span data-ttu-id="0b19e-115">**As2**: AS2-要 AS2-，以及其他的協議解析程式設定</span><span class="sxs-lookup"><span data-stu-id="0b19e-115">**For AS2**: AS2-To, AS2-From, and additional agreement resolver settings</span></span>  
  
-   <span data-ttu-id="0b19e-116">傳送埠關聯**傳送埠**頁面在單向協議索引標籤中的 X12、 EDIFACT 和 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="0b19e-116">Send port association from the **Send Ports** page in the one-way agreement tab for X12, EDIFACT, and AS2 agreements.</span></span>  
  
 <span data-ttu-id="0b19e-117">除去上方所列的屬性外，下列屬性都會匯出到 XML 範本檔案：</span><span class="sxs-lookup"><span data-stu-id="0b19e-117">Other than the properties listed above, the following properties will be exported to the XML template file:</span></span>  
  
-   <span data-ttu-id="0b19e-118">所有 編碼通訊協定 (X12、EDIFACT 或 AS2) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="0b19e-118">All settings related to the encoding protocol (X12, EDIFACT, or AS2).</span></span>  
  
-   <span data-ttu-id="0b19e-119">所有批次相關設定 (除批次識別碼外)。</span><span class="sxs-lookup"><span data-stu-id="0b19e-119">All the batch-related settings (other than the batch ID).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b19e-120">複製 屬性到目的地協議時，將會覆寫所有適用的屬性。</span><span class="sxs-lookup"><span data-stu-id="0b19e-120">All the applicable properties will be overwritten when you copy properties to the destination agreement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b19e-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="0b19e-121">In This Section</span></span>  
  
-   [<span data-ttu-id="0b19e-122">將協議屬性匯出至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="0b19e-122">Exporting Agreement Properties to an XML FIle</span></span>](../core/exporting-agreement-properties-to-an-xml-file.md)  
  
-   [<span data-ttu-id="0b19e-123">從 XML 檔案匯入協議屬性</span><span class="sxs-lookup"><span data-stu-id="0b19e-123">Importing Agreement Properties from an XML File</span></span>](../core/importing-agreement-properties-from-an-xml-file.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b19e-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b19e-124">See Also</span></span>  
 [<span data-ttu-id="0b19e-125">設定 EDI 屬性</span><span class="sxs-lookup"><span data-stu-id="0b19e-125">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)