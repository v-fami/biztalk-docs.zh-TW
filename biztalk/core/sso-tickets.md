---
title: SSO 票證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tickets [SSO]
ms.assetid: acf01422-4696-4301-b85f-7026e792bb5c
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e1ae40e43924faca6a5154b2b62a154fea1ea9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012711"
---
# <a name="sso-tickets"></a>SSO 票證
在使用者與各系統和應用程式互動的企業環境中，該環境很可能不會維護透過多個程序、產品和電腦的使用者內容。 此使用者內容對於提供單一登入功能而言是非常重要的，因為必須確認是由誰初始化原始要求。 為了解決這個問題，「企業單一登入」(SSO) 提供了 SSO 票證 (非 Kerberos 票證)，應用程式可以用來取得對應提出原始要求之使用者的認證。 預設不會啟用 SSO 票證。 如需啟用票證的詳細資訊，請參閱 <<c0> [ 如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md)。  
  
 驗證的 Windows 使用者提出要求時，SSO 系統會發出票證。 SSO 系統可以為提出要求的使用者或遠端使用者發出票證。 票證包含目前使用者的加密網域和使用者名稱，以及票證到期時間。 依照預設，SSO 系統發出票證之後，票證會在兩分鐘後到期。 SSO 系統管理員可以修改票證的到期時間。 SSO 系統管理員也可以設定「分支機構應用程式」層級的票證逾時。 如需詳細資訊，請參閱 <<c0> [ 如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md)。  
  
 在應用程式確認原始要求者的身分之後，應用程式就會贖回票證，以取得初始化要求分支機構應用程式的使用者認證。 應用程式從 SSO 系統贖回票證的方式有兩種：  
  
- **僅贖回。** 當應用程式初始化贖回票證的要求時，要求必須包含連接的分支機構應用程式之名稱以及票證本身。 只有特定分支機構應用程式的應用程式系統管理員、SSO 分支機構系統管理員或 SSO 系統管理員可以贖回票證。 您應該使用**僅贖回**所發行的應用程式與贖回票證的應用程式之間信任的子系統時。 只有指定分支機構應用程式的應用程式系統管理員可以為使用者贖回票證。  
  
- **驗證及贖回。** 票證包含 SSO 系統對其執行認證查詢的使用者相關資訊。 在此情況下，SSO 服務會在系統贖回票證之前，確認原始訊息的傳送者與票證的使用者是否相同。 Microsoft BizTalk Server 配接器實例會利用這個機制。  
  
  SSO 系統管理員可以在各個分支機構應用程式分別停用票證逾時。 雖然在舊版不建議這麼做，但這個版本可支援使用每個分支機構應用程式票證逾時。 此選項可以讓您在「分支機構應用程式」層級設定票證逾時。 若沒有指定，會使用在全域層級指定的票證逾時。  
  
  SSO 分支機構系統管理員可以分別指定每個分支機構應用程式上容許的票證以及所需的票證驗證。 不過，若 SSO 系統管理員在 SSO 系統層級指定需要驗證票證，SSO 分支機構系統管理員就無法在分支機構應用程式層級次關閉此選項。  
  
> [!IMPORTANT]
>  使用 SSO 票證時，您必須確保票證逾時值夠長，可以從發出票證持續到贖回票證。  
  
## <a name="see-also"></a>另請參閱  
 [管理使用者對應](../core/managing-user-mappings.md)