---
title: 為何為 BAM 撰寫程式碼？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4434f50a-e0a9-45e0-8c68-a059011e1296
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10b8ccb29d95daf8ccdf80d67faef3e50495af04
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22289886"
---
# <a name="why-write-code-for-bam"></a>為何為 BAM 撰寫程式碼？
在多數狀況下，您都可以使用 BAM 工具，而不需要撰寫自己的程式碼以執行追蹤功能。 這些工具包括適用於 Excel 的 BAM 增益集、[BAM 管理公用程式]，以及 [追蹤設定檔編輯器] \(TPE)。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 BAM 提供 BizTalk 協調流程和傳訊元件 (管線和連接埠) 的攔截器。 攔截器是一種檢測應用程式的軟體，使其能夠根據組態檔而以一般方式收集資料。 您可以使用 [追蹤設定檔編輯器] 來檢測應用程式，以便使用這些攔截器。 如需追蹤設定檔編輯器的詳細資訊，請參閱[追蹤設定檔編輯器](../core/tracking-profile-editor.md)。  
  
 不過，在兩種主要的案例中，您會發現使用 BAM API 檢測應用程式有很多優點：  
  
-   您想要監視的主控件沒有 BAM 攔截器。  
  
-   應用程式的複雜性不允許內建的攔截器。  
  
 沒有內建的攔截器時，您可以使用 BAM **EventStream** Api 來擷取感興趣的事件。  
  
> [!NOTE]
>  您可以結合 **EventStream** 類別與 **BAMInterceptor** 類別來建立自己的攔截器。 The BAM API SDK 範例說明您可以延伸的簡單一般攔截器。 藉由建構自己的攔截器，您可以檢測多個相似的處理序，而不需要為每個應用程式撰寫新的程式碼。 若要檢視 BAM API SDK 範例，請參閱[BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)。  
  
## <a name="see-also"></a>另請參閱  
 [實作 BAM 解決方案](../core/implementing-bam-solutions.md)