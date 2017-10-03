---
title: "如何建立密碼同步配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caa5bd13-efd9-4544-b5df-17d01c6ac5d8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c47381cc1ed71788673602c1db7eec5b5ac049ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-password-sync-adapter"></a>如何建立密碼同步配接器
密碼同步 (PS) 配接器是一套應用軟體，它使用「密碼同步協助程式」(Password Sync Helper) 元件傳送往來於「企業單一登入」(SSO) 的通知。 請注意，雖然 PS 協助程式元件使用 COM 介面和 .NET Framework 介面，但您的配接器不一定要是 COM 元件。 您可以將配接器設計為獨立程序、COM+ 應用程式或 Windows 服務。  
  
### <a name="to-create-a-password-sync-adapter"></a>若要建立密碼同步配接器  
  
1.  通知企業單一登入服務 (ENTSSO)，您的提供者正在使用 `ISSOPSWrapper.InitializeAdapter`。  
  
     `InitializeAdapter` 會通知 ENTSSO，表示目前有一個提供者 (通常與進行呼叫的提供者為同一個) 正在進行呼叫，因此該提供者會將密碼更新傳入及傳出系統。 您也可以使用`InitializeAdapter`啟動群組介面卡等其他資源。  
  
2.  使用 `ISSOPSWrapper.SendNotification` 傳送密碼更新到 ENTSSO。  
  
     您必須決定從非 Windows 系統接收密碼更新的方式。 接收更新之後，您可以使用 `SendNotification` 將資訊傳送到 ENTSSO。 請注意，`SendNotification`不限於傳送密碼更新： 的架構`SendNotification`也可讓您傳送其他類型的通知。  
  
3.  使用 `ISSOPSWrapper.ReceiveNotification` 向 ENTSSO 要求密碼更新。  
  
     因為密碼同步配接器是一種提取技術 (Pull technology)，所以 ENTSSO 永遠都不會呼叫您的配接器。 不過，您的配接器將定期呼叫 `ReceiveNotification`，以檢查是否有可用的密碼更新。 您可以選擇設定 `ReceiveNotification` 上的 WAIT 旗標。 設定 WAIT 將會封鎖執行緒，直到有通知為止。  
  
     請注意，ENTSSO 會以純文字傳送密碼變更到您的配接器。 保護密碼資訊免於不當的洩漏將是配接器的責任。 配接器也有責任保護自己免於其他無效來源的詐騙和攻擊，包括對「密碼同步協助程式」元件的詐騙。  
  
     在透過 `pReceiveNotification` 參數從 ENTSSO 接收密碼更新以後，您必須將此資訊傳送到您的非 Windows 系統。 和 `SendNotification` 一樣，您必須決定與遠端伺服器通訊的最佳方式。  
  
4.  使用 `ISSOPSWrapper.ShutdownAdapter` 關閉配接器。  
  
     `ShutdownApplication` 應是配接器所呼叫的最後一個方法，它表示配接器將不再對 ENTSSO 傳送或接收密碼更新。  
  
     請注意，當配接器為關閉時，ENTSSO 會緩衝使用者所變更的密碼，直到達到緩衝區的大小限制。  
  
## <a name="see-also"></a>另請參閱  
 [使用企業單一登入進行程式設計](../core/programming-with-enterprise-single-sign-on.md)   
 [同步處理密碼](../core/synchronizing-passwords.md)