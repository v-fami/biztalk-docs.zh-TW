---
title: "反向處理直接夥伴繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, partners
- process management solution tutorial, partner binding
ms.assetid: 4cf8717a-2098-46f4-8f58-9d05fb562e2a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6c9fe5e51f9f63ea098fa623dafbceeb670e75f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="inverse-direct-partner-binding"></a>反向處理直接夥伴繫結
商務程序管理解決方案的設計，可讓您變更訂單處理階段而不必停止應用程式。 為了減少處理階段 (**CableOrder1**， **CableOrder2**) 從處理序管理員 (**OrderManager**)，解決方案會使用針對不同的技術繫結這些協調流程之間的連接埠。  
  
 繫結的一般形式，指示繫結， **OrderManager**協調流程會使用處理階段協調流程做為值夥伴協調流程連接埠屬性。 像這樣的直接繫結中**OrderManager**協調流程會視強式名稱 （包含版本） 的處理階段。 這使得無法改變處理階段，而不需重新部署**OrderManager**協調流程。 如需直接繫結的詳細資訊，請參閱[連接埠繫結](../core/port-bindings.md)。 直接繫結可用以下方式來說明：  
  
 ![反向處理直接夥伴繫結的圖表](../core/media/bpm-inverse-direct-binding.gif "BPM_Inverse_Direct_Binding")  
  
 在反向處理直接夥伴繫結中，接收協調流程會指定繫結，而不是原始的協調流程。 上的連接埠**OrderManager**只會繫結至本身。 也就是在連接埠**OrderManager**指定**PartnerOrchestrationPort**屬性。 不過，處理階段協調流程會使用適合**OrderManager**做為值的連接埠**PartnerOrchestrationPort**屬性。 如此即可減少**OrderManager**來自處理階段協調流程的版本，並讓他們變更，而不重新部署**OrderManager**。 直接繫結不允許此種減少方式。 反向處理直接夥伴繫結可以下列方式顯示：  
  
 ![直接繫結的圖表](../core/media/bpm-direct-binding.gif "BPM_Direct_Binding")  
  
> [!NOTE]
>  反向處理直接繫結也允許以類似通訊群組清單的方式，與夥伴協調流程通訊。 **OrderManger**可以使用單一連接埠與所有階段通訊。 這讓您可以新增和移除階段，而不必重新設計協調流程。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [程序管理員邏輯](../core/process-manager-logic.md)