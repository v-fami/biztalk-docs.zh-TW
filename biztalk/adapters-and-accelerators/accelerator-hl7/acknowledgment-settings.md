---
title: 通知設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, configuring
- acknowledgements, acknowledgement types
- configuring, acknowledgements
ms.assetid: 99ab8caa-8788-4438-96db-8001a6523cc8
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8c1f19fa1a0d1abaad29f454f25f0d8608ed497
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967135"
---
# <a name="acknowledgment-settings"></a><span data-ttu-id="a05a3-102">通知設定</span><span class="sxs-lookup"><span data-stu-id="a05a3-102">Acknowledgment Settings</span></span>
<span data-ttu-id="a05a3-103">您使用**通知**索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 (底下的高階**合作對象** 索引標籤) 來設定通知 (ACK) 設定。</span><span class="sxs-lookup"><span data-stu-id="a05a3-103">You use the **Acknowledgment** tab of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer (under the high-level **Parties** tab) to configure acknowledgment (ACK) settings.</span></span>  
  
 <span data-ttu-id="a05a3-104">下列的通知類型可用：</span><span class="sxs-lookup"><span data-stu-id="a05a3-104">The following acknowledgment types are available:</span></span>  
  
- <span data-ttu-id="a05a3-105">**None**：</span><span class="sxs-lookup"><span data-stu-id="a05a3-105">**None**.</span></span> <span data-ttu-id="a05a3-106">如果您不想設定任何通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="a05a3-106">Select this option if you do not want to configure any acknowledgments.</span></span>  
  
- <span data-ttu-id="a05a3-107">**原始**。</span><span class="sxs-lookup"><span data-stu-id="a05a3-107">**Original**.</span></span> <span data-ttu-id="a05a3-108">選取此選項可設定**MSH1 – 欄位分隔符號**， **MSH2 – 編碼字元**，和**MSH8 – 安全性**只選項。</span><span class="sxs-lookup"><span data-stu-id="a05a3-108">Select this option to configure **MSH1 – Field Separator**, **MSH2 – Encoding Characters**, and the **MSH8 – Security** options only.</span></span>  
  
- <span data-ttu-id="a05a3-109">**增強**。</span><span class="sxs-lookup"><span data-stu-id="a05a3-109">**Enhanced**.</span></span> <span data-ttu-id="a05a3-110">選取此選項可設定所有可用的通知選項。</span><span class="sxs-lookup"><span data-stu-id="a05a3-110">Select this option to configure all available acknowledgment options.</span></span>  
  
- <span data-ttu-id="a05a3-111">**延後**。</span><span class="sxs-lookup"><span data-stu-id="a05a3-111">**Deferred**.</span></span> <span data-ttu-id="a05a3-112">選取此選項可設定**MSH1 – 欄位分隔符號**， **MSH2 – 編碼字元**，和**MSH8 – 安全性**只選項。</span><span class="sxs-lookup"><span data-stu-id="a05a3-112">Select this option to configure **MSH1 – Field Separator**, **MSH2 – Encoding Characters**, and **MSH8 – Security** options only.</span></span>  
  
- <span data-ttu-id="a05a3-113">**靜態**。</span><span class="sxs-lookup"><span data-stu-id="a05a3-113">**Static**.</span></span> <span data-ttu-id="a05a3-114">選取此選項可設定**成功**並**失敗**通知選項。</span><span class="sxs-lookup"><span data-stu-id="a05a3-114">Select this option to configure the **On success** and **On failure** acknowledgment options.</span></span>  
  
  <span data-ttu-id="a05a3-115">通知類型設定之後，您可以設定值，標頭欄位和通知，通知類型而定。</span><span class="sxs-lookup"><span data-stu-id="a05a3-115">Once the acknowledgment type is set, you can set values for header fields and acknowledgments, depending upon the acknowledgment type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a05a3-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="a05a3-116">In This Section</span></span>  
  
-   [<span data-ttu-id="a05a3-117">ACK 組態設定</span><span class="sxs-lookup"><span data-stu-id="a05a3-117">ACK Configuration Settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/ack-configuration-settings.md)  
  
-   [<span data-ttu-id="a05a3-118">設定訊息通知</span><span class="sxs-lookup"><span data-stu-id="a05a3-118">Configuring Message Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md)