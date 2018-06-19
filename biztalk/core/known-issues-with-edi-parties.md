---
title: EDI 合作對象的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 86475960-cdb2-4b39-817a-b5d834f498a9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fddda6dd62e8e3bd2d38574343b7fcb0e0d76f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261782"
---
# <a name="known-issues-with-edi-parties"></a>EDI 合作對象的已知問題
本節主題說明 EDI 合作對象和夥伴協議管理員的已知問題。  
  
## <a name="a-cache-refresh-period-delays-availability-of-a-changed-party-property"></a>快取重新整理週期延遲了已變更之合作對象屬性的可用時間  
 如果您在 PAM 中變更合作對象或全域屬性，必須等到每隔 15 分鐘的快取重新整理之後或是 BizTalk 服務重新啟動之後，才能在 BizTalk 執行階段中使用這些屬性。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 通知](../core/configuring-edi-acknowledgments.md)   
 [中協議 EDI 處理的角色](../core/the-role-of-agreements-in-edi-processing.md)   
 [設定 EDI 屬性](../core/configuring-edi-properties.md)   
 [設定全域或後援協議屬性](../core/configuring-global-or-fallback-agreement-properties.md)