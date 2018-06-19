---
title: 傳輸器介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffa6db3b-739e-438c-b410-8823a20eed82
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e922cd2526002306928b2eae3418185986ed741
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279718"
---
# <a name="transmitter-interfaces"></a><span data-ttu-id="4808e-102">傳輸器介面</span><span class="sxs-lookup"><span data-stu-id="4808e-102">Transmitter Interfaces</span></span>
<span data-ttu-id="4808e-103">除了強制的配接器介面，傳輸 （傳送） 配接器，就需要將實作**IBTTransmitter**有非批次或**IBTBatchTransmitter**如果不批次處理。</span><span class="sxs-lookup"><span data-stu-id="4808e-103">In addition to the mandatory adapter interfaces, transmit (send) adapters, need to implement either **IBTTransmitter** if they are non-batched or **IBTBatchTransmitter** if they are batched.</span></span>  
  
 <span data-ttu-id="4808e-104">下圖顯示批次處理和非批次處理的傳送配接器所需實作的介面。</span><span class="sxs-lookup"><span data-stu-id="4808e-104">The following figure shows the interfaces that batched and non-batched send adapters need to implement.</span></span>  
  
 ![](../core/media/transmitterinterfaces.gif "TransmitterInterfaces")