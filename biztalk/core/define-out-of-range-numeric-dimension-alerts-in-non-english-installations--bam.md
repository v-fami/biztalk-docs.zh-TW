---
title: 如何在非英文的安裝中定義超出範圍的數字維度警示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f1e0373-eadf-4c6d-9a38-a34d847f310f
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea63008680c026eded843e32a7b2c6ff26dc0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238686"
---
# <a name="how-to-define-out-of-range-numeric-dimension-alerts-in-non-english-installations"></a><span data-ttu-id="d1401-102">如何在非英文的安裝中定義超過範圍的數字維度警示</span><span class="sxs-lookup"><span data-stu-id="d1401-102">How to Define Out-of-Range Numeric Dimension Alerts In Non-English Installations</span></span>
<span data-ttu-id="d1401-103">當設定包含超出定義的數字範圍維度，在非英文的安裝上的值條件的警示，您必須手動修改 BAM 定義的當地語系化版本字串的**超出範圍**.</span><span class="sxs-lookup"><span data-stu-id="d1401-103">When setting alerts that include a condition for a value that is outside the defined numeric range dimension on non-English installations, you must manually modify the BAM definition with the localized version of the string **out of range**.</span></span>  
  
 <span data-ttu-id="d1401-104">下表列出值超過範圍的範例。</span><span class="sxs-lookup"><span data-stu-id="d1401-104">The following table lists examples of localized out-of-range values.</span></span>  
  
|<span data-ttu-id="d1401-105">語言代碼</span><span class="sxs-lookup"><span data-stu-id="d1401-105">Language code</span></span>|<span data-ttu-id="d1401-106">當地語系化字串</span><span class="sxs-lookup"><span data-stu-id="d1401-106">Localized string</span></span>|  
|-------------------|----------------------|  
|<span data-ttu-id="d1401-107">CN</span><span class="sxs-lookup"><span data-stu-id="d1401-107">CN</span></span>|<span data-ttu-id="d1401-108">超出范围</span><span class="sxs-lookup"><span data-stu-id="d1401-108">超出范围</span></span>|  
|<span data-ttu-id="d1401-109">DE</span><span class="sxs-lookup"><span data-stu-id="d1401-109">DE</span></span>|<span data-ttu-id="d1401-110">Außerhalb des gültigen Bereichs</span><span class="sxs-lookup"><span data-stu-id="d1401-110">Außerhalb des gültigen Bereichs</span></span>|  
|<span data-ttu-id="d1401-111">ES</span><span class="sxs-lookup"><span data-stu-id="d1401-111">ES</span></span>|<span data-ttu-id="d1401-112">Fuera de rango</span><span class="sxs-lookup"><span data-stu-id="d1401-112">Fuera de rango</span></span>|  
|<span data-ttu-id="d1401-113">FR</span><span class="sxs-lookup"><span data-stu-id="d1401-113">FR</span></span>|<span data-ttu-id="d1401-114">hors limites</span><span class="sxs-lookup"><span data-stu-id="d1401-114">hors limites</span></span>|  
|<span data-ttu-id="d1401-115">IT</span><span class="sxs-lookup"><span data-stu-id="d1401-115">IT</span></span>|<span data-ttu-id="d1401-116">Fuori intervallo</span><span class="sxs-lookup"><span data-stu-id="d1401-116">Fuori intervallo</span></span>|  
|<span data-ttu-id="d1401-117">JA</span><span class="sxs-lookup"><span data-stu-id="d1401-117">JA</span></span>|<span data-ttu-id="d1401-118">範囲外</span><span class="sxs-lookup"><span data-stu-id="d1401-118">範囲外</span></span>|  
|<span data-ttu-id="d1401-119">KO</span><span class="sxs-lookup"><span data-stu-id="d1401-119">KO</span></span>|<span data-ttu-id="d1401-120">범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1401-120">범위를 벗어남</span></span>|  
|<span data-ttu-id="d1401-121">TW</span><span class="sxs-lookup"><span data-stu-id="d1401-121">TW</span></span>|<span data-ttu-id="d1401-122">超過範圍</span><span class="sxs-lookup"><span data-stu-id="d1401-122">超過範圍</span></span>|  
  
### <a name="to-define-out-of-range-alerts-in-non-english-installations"></a><span data-ttu-id="d1401-123">若要在非英文的安裝中定義超過範圍的警示</span><span class="sxs-lookup"><span data-stu-id="d1401-123">To define out-of-range alerts in non-English installations</span></span>  
  
1.  <span data-ttu-id="d1401-124">瀏覽至包含 BAM 定義 xml 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d1401-124">Navigate to the folder containing your BAM definition xml file.</span></span>  
  
2.  <span data-ttu-id="d1401-125">利用文字編輯器或 XML 編輯器開啟 BAM 定義檔。</span><span class="sxs-lookup"><span data-stu-id="d1401-125">Using a text editor or an XML editor, open the BAM definition file.</span></span>  
  
3.  <span data-ttu-id="d1401-126">找出數字維度的 Slicer 維度。</span><span class="sxs-lookup"><span data-stu-id="d1401-126">Locate the slicer dimension for the numeric dimension.</span></span> <span data-ttu-id="d1401-127">例如，如果 slicer 維度名稱為**Alerts_NumDim**，您必須尋找下列節點：</span><span class="sxs-lookup"><span data-stu-id="d1401-127">For example, if your slicer dimension is named **Alerts_NumDim**, you would locate the following node:</span></span>  
  
    ```  
    <SlicerDimension Name="Alerts_NumDim">  
    <Level Name="(Out of Range)" />  
    </SlicerDimension>  
    ```  
  
4.  <span data-ttu-id="d1401-128">變更**超出範圍**至適當的字串值的當地語系化字串。</span><span class="sxs-lookup"><span data-stu-id="d1401-128">Change the **Out of Range** string value to the appropriate localized string.</span></span>  
  
5.  <span data-ttu-id="d1401-129">儲存檔案並部署定義。</span><span class="sxs-lookup"><span data-stu-id="d1401-129">Save the file and deploy the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1401-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1401-130">See Also</span></span>  
 <span data-ttu-id="d1401-131">[何謂 BAM 定義結構描述](../core/what-is-a-bam-definition-schema.md) </span><span class="sxs-lookup"><span data-stu-id="d1401-131">[What Is a BAM Definition Schema?](../core/what-is-a-bam-definition-schema.md) </span></span>  
 [<span data-ttu-id="d1401-132">如何部署 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="d1401-132">How to Deploy BAM Definitions</span></span>](../core/how-to-deploy-bam-definitions.md)