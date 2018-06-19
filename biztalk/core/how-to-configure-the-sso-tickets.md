---
title: 如何設定 SSO 票證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO], configuring tickets
- SSO, tickets
- tickets [SSO], configuring
ms.assetid: 32f0384b-ac79-4cce-b3f5-f4f8a73a673a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3b19d14a35d42c4a46bf9527a97f5bf749b875f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968644"
---
# <a name="how-to-configure-the-sso-tickets"></a>如何設定 SSO 票證
您可以使用 [MMC 嵌入式管理單元] 或命令列來控制整個「單一登入」系統的票證行為，包括是否允許票證以及系統是否必須驗證票證。  
  
 您可以使用 [Yes]、[No]、[On] 或 [Off] 來表示是否允許和/或驗證票證。 這些字與大小寫無關，不論您的語言設定為何都必須使用。  
  
 若您在遠端電腦上安裝 SSO 管理功能，則可執行遠端 IssueTicket 作業。 請注意，SSO 管理模組與執行階段模組 (ENTSSO 服務) 之間的所有流量都會加密。  
  
 只有在執行應用程式更新 (而不是在建立階段) 時，才可以使用命令列公用程式 ssomanage.exe 在「分支機構應用程式」層級指定票證逾時。  
  
 只有 SSO 系統管理員可以在 SSO 系統層級與分支機構應用程式層級中設定票證。  
  
 若票證在系統層級中停用，則也無法用於分支機構應用程式層級。 可以在系統層級中啟用票證，然後在分支機構應用程式層級中將它停用。  
  
 若在系統層級中啟用驗證，則分支機構應用程式層級也需要票證驗證。 可以在系統層級中停用驗證，然後在分支機構應用程式層級中將它啟用。  
  
 若在系統層級與分支機構應用程式層級都指定票證逾時，則在分支機構應用程式層級指定的值會用來決定票證到期時間。  
  
 如需有關票證和票證驗證的詳細資訊，請參閱[SSO 票證](../core/sso-tickets.md)。  
  
### <a name="to-configure-the-enterprise-single-sign-on-tickets-using-the-mmc-snap-in-for-the-affiliate-application"></a>使用 MMC 嵌入式管理單元為分支機構應用程式設定企業單一登入票證  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 範圍 窗格的 ENTSSO MMC 嵌入式管理單元，依序展開**分支機構應用程式**節點。  
  
3.  以滑鼠右鍵按一下**分支機構應用程式**，然後按一下 **屬性**。  
  
4.  按一下**選項** 索引標籤。  
  
5.  選取**允許票證**依適當情況設定票證逾時。  
  
### <a name="to-configure-the-enterprise-single-sign-on-system-level-tickets-using-the-command-line"></a>使用命令列設定企業單一登入系統層級票證  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – 票證\<允許是/否\> *\<驗證是/否\>***，其中*\<允許是/否\>* 表示，系統是否允許票證和*\<驗證是/否\>* 指出是否需要重新驗證後贖回票證.  
  
    > [!NOTE]
    >  您可以使用 [yes]、[no]、[on] 或 [off] 來表示是否允許和/或驗證票證。 這些字與大小寫無關，不論您的語言設定為何都必須使用。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [瞭解 SSO](../core/understanding-sso.md)   
 [使用 SSO](../core/using-sso.md)