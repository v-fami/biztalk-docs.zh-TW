---
title: 如何還原憑證存放區 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c6f7551-d119-4668-9b52-6013f69a0302
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaeee6b762cf5af15ca7cba34864abd86682d4df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254694"
---
# <a name="how-to-restore-the-certificate-store"></a>如何還原憑證存放區
復原過程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須還原憑證存放區。 如果您要復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Standard Edition 中，您必須使用此程序來還原憑證存放區。 您不需要復原所有其他版本時，執行此程序[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]因為復原程序會自動還原您的憑證存放區。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「系統管理員」群組成員的身分登入，才能執行此程序。  
  
### <a name="to-restore-the-certificate-store-biztalk-server-standard-edition"></a>若要還原憑證存放區 (BizTalk Server Standard Edition)  
  
1.  按一下**啟動**，按一下 **所有程式**，然後按一下  **Internet Explorer**。  
  
2.  在**工具**功能表上，按一下 **網際網路選項**。  
  
3.  在**網際網路選項**對話方塊中，按一下 **內容**索引標籤，然後再按一下**憑證**。  
  
4.  在**憑證**對話方塊中，按一下 **其他人**索引標籤，然後再按一下**匯入**。  
  
5.  在**憑證匯入精靈**，按一下 **取消**。  
  
     這會建立**AddressBook**登錄中的登錄區。  
  
6.  在**憑證**對話方塊中，按一下 **關閉**。  
  
7.  在**網際網路選項**對話方塊中，按一下 **確定**。  
  
8.  按一下**檔案**，然後按一下 **關閉**結束 Internet Explorer。  
  
9. 按一下**啟動**，按一下 **執行**，型別**regedit**，然後按一下 **確定**。  
  
10. 在「登錄編輯程式」中，瀏覽至下列登錄機碼：  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates**  
  
11. 確認**AddressBook**登錄區存在。  
  
## <a name="see-also"></a>另請參閱  
 [復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md)