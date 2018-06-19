---
title: 限制 BizTalk adapter for mySAP Business Suite |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, limitations of
- IDOC, sending an IDOC to an SAP system
ms.assetid: 1ca1e0cf-7ae7-4a8b-8363-e5f3746e8e26
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d392178cd49918151f0ad86c73a5fcba712d6b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217078"
---
# <a name="limitations-of-biztalk-adapter-for-mysap-business-suite"></a>BizTalk adapter for mySAP Business Suite 的限制

## <a name="limitations-list"></a>限制清單
下列已知的限制[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:  
  
-   [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不是與 Microsoft BizTalk Adapter for mySAP Business Suite，配接器之前的版本相容。 這一版的配接器不支援傳送和接收訊息，需要使用舊版的配接器所產生的結構描述。  
  
-   [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援具有複雜的參數類型，包括 ITAB II （階層式） 的資料表類型的 Rfc。  
  
-   [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援具有自訂 ABAP 類型的 Rfc。  
  
-   由於處理基礎的用戶端程式庫，逾時問題[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援命令，並連接逾時。  
  
-   如果您變更執行 BizTalk Server 主控件之電腦的系統時間，時間是不會自動更新 BizTalk Server 主控件中。 這可能會導致不正確的行為，使用 BizTalk Server 接收埠的輸入作業。 因應措施，您必須重新啟動後已變更其執行之電腦的系統時間有接收埠，主控件執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)