---
title: 停止處理在來源系統上的應用程式 |Microsoft Docs
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
ms.openlocfilehash: c92fe07371be2abb44c314eb77eb38c6c853bebe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982455"
---
# <a name="stopping-application-processing-on-the-source-system"></a>停止處理在來源系統上的應用程式
應用程式處理應停止時來源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段伺服器都仍然能夠參與以使用現有的資料庫伺服器的文件處理。 在此案例中，處理活動必須先停止，因此可完成保持一致還原作業。  
  
 若要停止來源系統上的應用程式處理，請確定沒有連線可開啟生產環境之間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 請遵循下列步驟來停止對實際執行的應用程式處理[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦：  
  
1. 停用所有接收位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk 群組中的電腦。 請記下的所有接收位置，讓這些接收位置已停用來重新啟用稍後。 這將會停止[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理內送訊息。  
  
2. 停止所有的主控件執行個體上執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中的電腦。 這可以從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 記下 已停止，以便這些主控件執行個體可以稍後再重新啟動所有主控件執行個體。  
  
3. 停止所有[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Agent 作業的相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
4. 如果 BAM 正在使用中，停用任何 BAM cube 更新和資料維護 SSIS 封裝。 做法是使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio。  
  
5. 停止 Analysis Services[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 這可以藉由停止 MSSQLServerOLAPService 的所有執行個體上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 安裝所在的電腦。  
  
6. 停止任何其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務可能執行的服務管理員中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦在群組中，比方說，「 企業單一登入服務 」 和 「 規則引擎更新服務。 記下 已停止，讓它們可以重新啟動更新版本的服務。  
  
7. 關閉所有應用程式連接到[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 這包括的執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中， [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]，和任何其他已安裝 BizTalk 應用程式。  
  
8. 確認沒有任何資料庫的活動所產生[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio 來查看哪些程序會連接到[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 這可以藉由展開**管理**，並按兩下**活動監視器**在[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio。 然後按一下以選取**處理序資訊**。 使用系統預存程序，或者**sp_who**或**sp_who2**來識別任何開放連線[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 如果有任何連接的程序，找出它們，並終止它們通常;最後的手段，以滑鼠右鍵按一下每個處理序中的**處理序資訊** 窗格中的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio，然後按一下**終止處理序**終止連線。  
  
9. 其他資料庫的處理可能發生在應用程式資料庫。 如果要還原這些資料庫，請確定所有處理都已都停止。  
  
## <a name="see-also"></a>另請參閱  
 [還原 BizTalk 群組](../technical-guides/restoring-the-biztalk-group.md)