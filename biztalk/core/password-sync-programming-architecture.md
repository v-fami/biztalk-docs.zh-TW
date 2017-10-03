---
title: "密碼同步程式設計架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679edbf1-fb08-4472-b366-3e1d361b20e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebb68af3624b19a5a5385902d6a0131cfe28acb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="password-sync-programming-architecture"></a>密碼同步程式設計架構
密碼同步配接器會使用提取模型的企業單一登入系統的其餘部分互動： 也就是配接器主動接收密碼變更從 「 企業單一登入 (ENTSSO) 服務和也非 Windows 系統。 同理，配接器會將接收到的密碼變更從一個系統推到另一個。 與此模型中，您的配接器互動具有三個架構的元件： ENTSSO 架構、 密碼同步 (PS) 協助程式元件，以及指定的非 Windows 系統。  
  
## <a name="enterprise-single-sign-on-architecture"></a>企業單一登入架構  
 ENTSSO 是實作「企業單一登入」技術的服務，和配接器在相同系統上作為本機服務執行。 因此，配接器與 ENTSSO 之間的通訊永遠為本機。 但是，密碼同步配接器與 ENTSSO 服務在不同的程序中執行。  
  
 ENTSSO 使用組態存放區以儲存配接器的組態資訊。 組態存放區應用程式的「應用程式使用者」帳戶對應到存取帳戶。 當配接器呼叫 ENTSSO 時，ENTSSO 會檢查配接器是否在該配接器的設定存取帳戶內。 存取帳戶必須為 (本機或網域) 群組帳戶。  
  
 因為 ENTSSO 儲存配接器的相關資訊，所以配接器可透過其配接器名稱向 ENTSSO 識別自己。 配接器名稱對應到組態存放區應用程式名稱，以及用以儲存配接器屬性的組態存放區識別項。 因此，配接器只需要知道它們的配接器名稱便可存取組態資訊，以及在執行階段正確地向 ENTSSO 系統識別自己。  
  
## <a name="password-sync-helper"></a>密碼同步協助程式  
 「密碼同步 (PS) 協助程式」是 ENTSSO 提供的 COM 元件。 「PS 協助程式」以內含式與密碼同步配接器執行，並公開 ISSOPSWrapper。 您的配接器可以呼叫任一個介面，以便和 ENTSSO 服務通訊。 「PS 協助程式」使用加密的 (封包私密性) 輕量型遠端程序呼叫 (LRPC) 與 ENTSSO 來回傳遞通訊。 通訊主要用於密碼更新，但是您也可以使用介面，在配接器和 ENTSSO 之間傳遞其他類型的通知。 因為「PS 協助程式」的每個程序都以單一值執行，所以多個配接器可以從相同的配接器程序中呼叫相同的「PS 協助程式」物件。 如需有關以程式設計方式使用 「 PS 協助程式的詳細資訊，請參閱[同步處理密碼](../core/synchronizing-passwords.md)。  
  
## <a name="non-windows-system"></a>非 Windows 系統  
 非 Windows 系統是與您的配接器互動之遠端電腦。 您可自行決定與非 Windows 系統互動的方式。  
  
## <a name="see-also"></a>另請參閱  
 [密碼同步配接器](../core/password-sync-adapters.md)