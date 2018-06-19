---
title: 停止處理在來源系統上的應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cde5fc62-4bc2-4ef0-81bc-c7d39ff36cb6
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70fe980e3f29e2bd4cf13aa2b74a1923126fcec2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302350"
---
# <a name="stopping-application-processing-on-the-source-system"></a>停止處理在來源系統上的應用程式
應用程式處理應該停止時的來源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段伺服器都仍然能夠參與使用現有的資料庫伺服器的文件處理。 在此案例中，處理活動必須先停止如此便可以完成一致的還原作業。  
  
 若要停止應用程式處理來源系統上，請確定所有連接都都會開啟生產環境之間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 請遵循下列步驟來停止對實際執行的應用程式處理[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦：  
  
1.  停用所有接收位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk 群組中的電腦。 請記下所有接收位置已停用，讓這些接收位置來重新啟用更新版本。 這會停止[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法處理內送訊息。  
  
2.  停止所有的主控件執行個體上執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中的電腦。 這可藉由[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 記下 已停止，以便可以稍後重新啟動這些主控件執行個體的所有主控件執行個體。  
  
3.  停止所有[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
4.  如果 BAM 正在使用中，停用任何 BAM cube 更新及資料維護 SSIS 封裝。 這可以經由使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio。  
  
5.  停止 Analysis Services 上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 這可藉由來停止 MSSQLServerOLAPService 的所有執行個體上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]安裝 Analysis Services 的電腦。  
  
6.  停止任何其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能執行的服務管理員中的服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中的電腦，例如 「 企業單一登入服務 」 和 「 規則引擎更新服務。 記下以便它們可以稍後重新啟動已停止的服務。  
  
7.  關閉所有應用程式連接到[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 這包括執行個體的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中， [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]，和任何其他已安裝 BizTalk 應用程式。  
  
8.  請確認沒有資料庫活動所產生[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio 來查看哪些程序會連接到[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 這可藉由擴充**管理**按兩下**活動監視器**中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio。 然後按一下以選取**處理序資訊**。 使用系統預存程序，或者**sp_who**或**sp_who2**來識別任何開啟的連接[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 如果有任何連接的程序，找到這些服務，並通常; 予以終止最後的方法，以滑鼠右鍵按一下中的每個處理序或**處理序資訊** 窗格中的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio，然後按一下**終止處理序**終止連線。  
  
9. 其他資料庫的處理可能會發生在應用程式資料庫。 如果要還原這些資料庫，請確定所有處理都會都停止。  
  
## <a name="see-also"></a>另請參閱  
 [還原 BizTalk 群組](../technical-guides/restoring-the-biztalk-group.md)