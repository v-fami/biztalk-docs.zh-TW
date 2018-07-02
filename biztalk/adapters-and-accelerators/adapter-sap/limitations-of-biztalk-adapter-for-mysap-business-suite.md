---
title: BizTalk Adapter for mySAP Business Suite 的限制 |Microsoft Docs
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
ms.openlocfilehash: f289d1f70005e8b4caa0e7c739522cc5590bca58
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973711"
---
# <a name="limitations-of-biztalk-adapter-for-mysap-business-suite"></a>BizTalk Adapter for mySAP Business Suite 的限制

## <a name="limitations-list"></a>限制清單
下列已知的限制[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:  
  
- [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不是與 Microsoft BizTalk Adapter for mySAP Business Suite，配接器的舊版相容。 這一版的配接器不支援傳送和接收有使用舊版配接器所產生的結構描述的訊息。  
  
- [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援 Rfc 使用複雜的參數類型，包括 ITAB II （階層式） 的資料表類型。  
  
- [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援 Rfc 擁有自訂的 ABAP 型別。  
  
- 因為處理基礎的用戶端程式庫，逾時問題而[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援命令，並連接逾時。  
  
- 如果您變更執行 BizTalk Server 主控件之電腦的系統時間，時間不會更新會自動在 BizTalk Server 主控件。 這可能會導致不正確的行為，使用 BizTalk Server 接收埠的輸入作業。 因應措施，您必須重新啟動後已執行它的電腦的系統時間已接收埠，主控件執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)