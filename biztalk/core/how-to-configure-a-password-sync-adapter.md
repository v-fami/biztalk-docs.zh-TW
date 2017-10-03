---
title: "如何設定密碼同步配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0effdc9b-4aee-4674-90c5-03dfd7cc4cd6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f0be0146e905ef291942bd30adc111eff89e989
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-password-sync-adapter"></a>如何設定密碼同步配接器
完成建立密碼同步配接器之後，必須將配接器載入系統。 此外，必須通知「企業單一登入」(ENTSSO) 和組態存放區，您的應用程式為密碼同步配接器。 您必須向組態存放區，基於安全性考量： 您的配接器將會要求更新密碼與其他認證。 因此，ENTSSO 必須知道是否已允許指定的配接器要求這類權限。  
  
### <a name="to-configure-a-password-sync-adapter"></a>設定密碼同步配接器  
  
1.  使用 SSOPS 工具建立具有組態存放區的配接器。  
  
     使用 SSOPS 將 XML 組態檔載入組態資料庫，該資料庫會向「企業單一登入」描述您的應用程式。  
  
2.  在建立具有組態資料庫的配接器之後，您可以使用 `ISSOPSAdmin.SetAdapterProperties` 來修改配接器資訊。  
  
     雖然這兩個方法很相似，不過 `SetAdapterProperties` 會在組態資訊變更時傳送訊息至配接器。  
  
3.  若要刪除配接器，可使用 ISSOAdmin.DeleteApplication。  
  
## <a name="see-also"></a>另請參閱  
 [同步處理密碼](../core/synchronizing-passwords.md)