---
title: FIN 回應對帳疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, troubleshooting
- troubleshooting, FIN Response Reconciliation
ms.assetid: f62326aa-9a4e-4941-a9bb-20bde980f99e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a92812086f191d5777b387d9861b32a3147c1e96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207414"
---
# <a name="fin-response-reconciliation-troubleshooting"></a>FIN 回應對帳疑難排解
## <a name="the-frr-bam-view-does-not-show-the-message-type-of-a-message"></a>FRR BAM 檢視不會顯示一則訊息的訊息類型  
  
### <a name="symptom"></a>徵兆  
 MRSR 站台中 FRR BAM 檢視不會顯示一個或多個訊息的訊息類型。 顯示的訊息或訊息的所有其他資料，且會顯示訊息類型的所有其他訊息類型的執行個體。  
  
### <a name="possible-cause"></a>可能的原因  
 FRRMessageOut 活動不會記錄 F21 訊息 (Ack/NAKs) 的訊息類型。  
  
### <a name="solution"></a>方案  
 如果您遇到這個問題，解譯為 F21 訊息 MRSR 站台中 FRR BAM 檢視中所列出的訊息類型沒有任何訊息。  
  
## <a name="deploying-system-level-schemas-in-a-project-generates-an-error"></a>部署系統層級專案中的結構描述會產生錯誤  
  
### <a name="symptom"></a>徵兆  
 當您嘗試將部署系統層級中的結構描述 FrrSchemas.dll 專案中時，您會收到錯誤。 如需這些結構描述的清單，請參閱[FIN 回應類型](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md)。  
  
### <a name="possible-cause"></a>可能的原因  
 系統層級中的結構描述 FrrSchemas.dll FrrSchemas.dll 中已部署。 嘗試將其部署一次產生錯誤。  
  
### <a name="solution"></a>方案  
 沒有需要部署系統層級中的結構描述 FrrSchemas.dll。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解： 問題與解決方式](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)