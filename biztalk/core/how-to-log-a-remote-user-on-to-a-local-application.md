---
title: 如何將遠端使用者登入本機應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 886ee7cb-e6ba-476a-bea9-4bb4c22bf94e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f638007c3c4eb1f85a5b5a701dd2b456c2d220d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254214"
---
# <a name="how-to-log-a-remote-user-on-to-a-local-application"></a>如何將遠端使用者登入本機應用程式
「企業單一登入」(ENTSSO) 服務的另一個主要功能是支援主控件初始化的程序 (HIP)。 當遠端使用者嘗試存取本機 Windows 資源時，ENTSSO 會與 HIP 互動。 使用 ENTSSO 時，您可以接收來自主控件使用者的要求，以及對本機 Windows 應用程式的存取要求。  
  
## <a name="log-a-remote-user-on-to-a-local-windows-application"></a>遠端使用者登入本機 Windows 應用程式  
  
1.  接收來自遠端使用者的要求。  
  
     您必須決定如何接收遠端使用者的要求。  
  
2.  使用 `ISSOLookup2.LogonExternalUser` 要求授與遠端使用者存取指定之分支機構應用程式的權限。  
  
     `LogonExternalUser` 會傳遞外部使用者希望存取的應用程式名稱、外部使用者名稱、外部使用者的相關認證，以及任何相關旗標。 如果成功的話，`LogonExternalUser` 會傳回 Windows 存取語彙基元的控制代碼。  
  
     遠端使用者必須已經通過「單一登入」資料庫中的識別、在此資料庫中具有認證，並與分支機構應用程式建立關聯。 否則，`LogonExternalUser` 會傳回錯誤。 您可以使用「密碼同步」讓使用者名稱和認證保持在最新的狀態。  
  
     另外，您也必須啟用通訊協定轉換。  
  
3.  使用 `LogonExternalUser` 傳回的 Windows 控制代碼來模擬此語彙基元所代表的使用者。  
  
## <a name="see-also"></a>另請參閱  
 [如何登入非 Windows 應用程式的本機使用者](../core/how-to-log-a-local-user-on-to-a-non-windows-application.md)   
 **ISSOLookup2.LogonExternalUser 方法**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]