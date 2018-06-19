---
title: EDI 訊息驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71f34561-d280-48bb-b1dd-ce37b87c5023
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21439969bc8e23b5b9901077c14a98128aa64c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238822"
---
# <a name="edi-message-validation"></a><span data-ttu-id="d3976-102">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="d3976-102">EDI Message Validation</span></span>
<span data-ttu-id="d3976-103">EDI 資料是以分隔檔案形式 (不含自我描述標記) 傳輸，因此，編碼規則會強制套用限制格式設定規則，確保目的地應用程式可以成功地剖析和使用該資訊進行下游處理。</span><span class="sxs-lookup"><span data-stu-id="d3976-103">EDI data is transmitted as delimited files (without self describing tags) and therefore the encoding rules enforce strict formatting rules to ensure the destination application is able to successfully parse and consume the information for downstream processing.</span></span>  
  
 <span data-ttu-id="d3976-104">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 的 EDI 接收管線和 EDI 傳送管線，會與 AS2 一起執行一連串的驗證。</span><span class="sxs-lookup"><span data-stu-id="d3976-104">The EDI receive pipeline and EDI send pipeline in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 perform a series of validations.</span></span> <span data-ttu-id="d3976-105">有些驗證一定會執行，有些驗證則要在協議屬性或是結構描述中有啟用時才會執行。</span><span class="sxs-lookup"><span data-stu-id="d3976-105">Some are always performed; others are performed if enabled in agreement properties or in the schema.</span></span> <span data-ttu-id="d3976-106">如需有關驗證的設定方式的詳細資訊，請參閱[如何驗證 EDI 交換設定](../core/how-validation-of-an-edi-interchange-is-configured.md)。</span><span class="sxs-lookup"><span data-stu-id="d3976-106">For more information about how validation is configured, see [How Validation of an EDI Interchange Is Configured](../core/how-validation-of-an-edi-interchange-is-configured.md).</span></span>  
  
 <span data-ttu-id="d3976-107">EDI 交換的驗證作業包括了幾種不同的驗證方式，如下列主題所述。</span><span class="sxs-lookup"><span data-stu-id="d3976-107">Validation of an EDI interchange involves several different kinds of validation, as described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3976-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="d3976-108">In This Section</span></span>  
  
-   [<span data-ttu-id="d3976-109">EDI 交換的驗證設定的方式</span><span class="sxs-lookup"><span data-stu-id="d3976-109">How Validation of an EDI Interchange Is Configured</span></span>](../core/how-validation-of-an-edi-interchange-is-configured.md)  
  
-   [<span data-ttu-id="d3976-110">EDI 結構驗證</span><span class="sxs-lookup"><span data-stu-id="d3976-110">EDI Structural Validation</span></span>](../core/edi-structural-validation.md)  
  
-   [<span data-ttu-id="d3976-111">協議屬性驗證</span><span class="sxs-lookup"><span data-stu-id="d3976-111">Agreement Properties Validation</span></span>](../core/agreement-properties-validation.md)  
  
-   [<span data-ttu-id="d3976-112">EDI 類型 （資料元素） 驗證</span><span class="sxs-lookup"><span data-stu-id="d3976-112">EDI Type (Data Element) Validation</span></span>](../core/edi-type-data-element-validation.md)  
  
-   [<span data-ttu-id="d3976-113">擴充 (BTS-XSD) 驗證</span><span class="sxs-lookup"><span data-stu-id="d3976-113">Extended (BTS-XSD) Validation</span></span>](../core/extended-bts-xsd-validation.md)  
  
-   [<span data-ttu-id="d3976-114">結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="d3976-114">Schema Validation</span></span>](../core/schema-validation2.md)  
  
-   [<span data-ttu-id="d3976-115">交叉驗證欄位區段</span><span class="sxs-lookup"><span data-stu-id="d3976-115">Cross Field-Segment Validation</span></span>](../core/cross-field-segment-validation.md)