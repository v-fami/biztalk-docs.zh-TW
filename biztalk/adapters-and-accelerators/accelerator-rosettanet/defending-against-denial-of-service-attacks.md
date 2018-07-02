---
title: 對抗阻絕服務攻擊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, denial-of-service attacks
- denial-of-service attacks
ms.assetid: 63342d7a-a5df-4e11-9037-93175d8f7ea7
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab2aa48e126aafc7b2202547fd72806b5d471ef4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976919"
---
# <a name="defending-against-denial-of-service-attacks"></a>對抗阻絕服務攻擊
有人可能會開始安裝 Microsoft® 阻絕服務攻擊[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]負荷過重的 RNIFReceive.aspx 接收頁面。 他們只要傳送大量空白訊息至該頁面，便可進行拒絕服務攻擊。 若稍不留意，這類攻擊可能會使事件日誌充滿大量由 ASPX 接收頁面發出的事件。  
  
## <a name="defending-against-an-attack"></a>對抗攻擊  
 若要防護您的伺服器避免拒絕服務攻擊，建議您讓事件日誌保持合理的大小，並著手處理大量事件的情形。 您可以設定事件日誌大小的上限、選取覆寫事件的方式，或者使用 [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]® Management Instrumentation (WMI) 管理日誌的大小，以達到此目的。 如需詳細資訊，請參閱 Microsoft 說明[!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)]™。  
  
## <a name="see-also"></a>另請參閱  
 [管理設定、憑證、資料庫和安全性](manage-configuration-certificates-databases-security.md)