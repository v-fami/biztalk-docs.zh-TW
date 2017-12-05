---
title: "EDI 字元集支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4f4492b-8cbe-48ed-810a-3e73e1cb5996
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da903e0cde796c6b12c30ea32dfe4012215a231e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="edi-character-set-support"></a><span data-ttu-id="d6451-102">EDI 字元集支援</span><span class="sxs-lookup"><span data-stu-id="d6451-102">EDI Character Set Support</span></span>
<span data-ttu-id="d6451-103">本主題說明中的 BizTalk Server EDI 功能支援的字元集。</span><span class="sxs-lookup"><span data-stu-id="d6451-103">This topic indicates which character sets are supported in the EDI features of BizTalk Server.</span></span>  
  
|<span data-ttu-id="d6451-104">EDI 編碼</span><span class="sxs-lookup"><span data-stu-id="d6451-104">EDI Encoding</span></span>|<span data-ttu-id="d6451-105">支援的字元集</span><span class="sxs-lookup"><span data-stu-id="d6451-105">Supported Character Sets</span></span>|  
|------------------|------------------------------|  
|<span data-ttu-id="d6451-106">X12 （包括 HIPAA）</span><span class="sxs-lookup"><span data-stu-id="d6451-106">X12 (including HIPAA)</span></span>|<span data-ttu-id="d6451-107">X12 - 基本字元集 (ASCII 的子集)</span><span class="sxs-lookup"><span data-stu-id="d6451-107">X12 - Basic character set (subset of ASCII)</span></span>|  
|-|<span data-ttu-id="d6451-108">X12- 擴充的字元集 (ASCII 的子集，同時包含 ISO8859-1 字元)</span><span class="sxs-lookup"><span data-stu-id="d6451-108">X12- Extended character set (subset of ASCII and also includes ISO8859-1 chars)</span></span>|  
|-|<span data-ttu-id="d6451-109">UTF8/UNICODE</span><span class="sxs-lookup"><span data-stu-id="d6451-109">UTF8/UNICODE</span></span>|  
|<span data-ttu-id="d6451-110">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="d6451-110">EDIFACT</span></span>|<span data-ttu-id="d6451-111">UNOA</span><span class="sxs-lookup"><span data-stu-id="d6451-111">UNOA</span></span>|  
|-|<span data-ttu-id="d6451-112">UNOB</span><span class="sxs-lookup"><span data-stu-id="d6451-112">UNOB</span></span>|  
|-|<span data-ttu-id="d6451-113">UNOC-ISO 8859-1： 資訊處理-第 1 部分： 拉丁字母 [否]。</span><span class="sxs-lookup"><span data-stu-id="d6451-113">UNOC- ISO 8859-1 : Information processing - Part 1: Latin alphabet No.</span></span> <span data-ttu-id="d6451-114">1</span><span class="sxs-lookup"><span data-stu-id="d6451-114">1</span></span>|  
|-|<span data-ttu-id="d6451-115">KECA - KS_C_5601-1987 (Windows 949 字碼頁)</span><span class="sxs-lookup"><span data-stu-id="d6451-115">KECA - KS_C_5601-1987 (Windows 949 Code page)</span></span>|  
|-|<span data-ttu-id="d6451-116">UNOX (ISO2022 – JP)</span><span class="sxs-lookup"><span data-stu-id="d6451-116">UNOX (ISO2022 – JP)</span></span>|  
|-|<span data-ttu-id="d6451-117">UNOY-UTF8 編碼資料**附註：** UNOD 到 UNOK 字元集設定的支援 UTF8 編碼的資料也支援。</span><span class="sxs-lookup"><span data-stu-id="d6451-117">UNOY- UTF8 encoded data **Note:**  The UNOD through UNOK character sets that support UTF8 encoded data are also supported.</span></span>|  
  
## <a name="setting-the-edi-character-set"></a><span data-ttu-id="d6451-118">設定 EDI 字元集</span><span class="sxs-lookup"><span data-stu-id="d6451-118">Setting the EDI Character Set</span></span>  
 <span data-ttu-id="d6451-119">對於 X12 編碼交換，您可以設定 CharacterSet 管線屬性，來設定管線的字元集。</span><span class="sxs-lookup"><span data-stu-id="d6451-119">For X12 encoded interchanges, you can set the character set for a pipeline by setting the CharacterSet pipeline property.</span></span> <span data-ttu-id="d6451-120">如需詳細資訊，請參閱[設定 EDI 管線屬性](../core/configuring-edi-pipeline-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d6451-120">For more information, see [Configuring EDI Pipeline Properties](../core/configuring-edi-pipeline-properties.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6451-121">在 [BizTalk Server 管理主控台] 中，[X12 EDI 屬性] 對話方塊的 [產生 X12 交換信封] 頁面上有一個 X12 字元集控制項，但該控制項只是用來驗證 [EDI 屬性] 對話方塊中的屬性輸入值。</span><span class="sxs-lookup"><span data-stu-id="d6451-121">There is an X12 character set control in the X12 Interchange Envelope Generation page of the X12 EDI Properties dialog box in the BizTalk Server Administration console, but that control is only used to validate the values entered for the properties in the EDI Properties dialog box.</span></span>  
  
 <span data-ttu-id="d6451-122">對於 EDIFACT 編碼交換，您可以在 [做為交換接收者的合作對象] 的 [UNB 區段定義] 屬性頁中設定 UNB1.1 合作屬性，來設定合作對象的字元集。</span><span class="sxs-lookup"><span data-stu-id="d6451-122">For EDIFACT encoded interchanges, you can set the character set for a party by setting the UNB1.1 party property in the UNB Segment Definition property page for the party as interchange receiver.</span></span> <span data-ttu-id="d6451-123">內送交換中使用的編碼，則由交換之標頭內的 UNB1.1 欄位值決定。</span><span class="sxs-lookup"><span data-stu-id="d6451-123">The encoding used in an incoming interchange is determined by the value of the UNB1.1 field in the header of the interchange.</span></span> <span data-ttu-id="d6451-124">如需詳細資訊，請參閱[設定信封 （EDIFACT 交易集設定）](../core/configuring-envelopes-edifact-transaction-set-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="d6451-124">For more information, see [Configuring Envelopes (EDIFACT-Transaction Set Settings)](../core/configuring-envelopes-edifact-transaction-set-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6451-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6451-125">See Also</span></span>  
 <span data-ttu-id="d6451-126">[設定 EDI 管線屬性](../core/configuring-edi-pipeline-properties.md) </span><span class="sxs-lookup"><span data-stu-id="d6451-126">[Configuring EDI Pipeline Properties](../core/configuring-edi-pipeline-properties.md) </span></span>  
 [<span data-ttu-id="d6451-127">設定信封 (EDIFACT 交易集設定)</span><span class="sxs-lookup"><span data-stu-id="d6451-127">Configuring Envelopes (EDIFACT-Transaction Set Settings)</span></span>](../core/configuring-envelopes-edifact-transaction-set-settings.md)