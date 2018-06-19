---
title: 如何設定強式名稱組件金鑰檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5778a8ec-f5f7-4ae1-a57e-99f6503f044c
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec807cf6b596f7e89f607ebeb56700c59134c211
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968804"
---
# <a name="how-to-configure-a-strong-name-assembly-key-file"></a>如何設定強式名稱組件金鑰檔案
在部署 BizTalk 解決方案的程序中，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 會先建置組件。 部署程序要求每個組件都應經過強式簽署。 您可以將專案與強式名稱組件金鑰檔案產生關聯，即可強式簽署組件。 如果您還沒有，部署從解決方案之前[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，來產生強式名稱組件金鑰檔案，並將它指派給每個專案方案中使用下列程序。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入帳戶的成員[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員群組。 此外，您的帳戶必須有全域組件快取 (GAC) 的寫入權限。 本機電腦上的「系統管理員」帳戶具有這項權限。  
  
### <a name="to-configure-a-strong-name-assembly-key-file"></a>若要設定強式名稱組件金鑰檔案  
  
1.  啟動**Visual Studio 命令提示字元**。  
  
2.  在命令提示字元中，切換到您想要儲存金鑰檔案的資料夾，再輸入下列命令，然後按下 ENTER：  
  
     **sn /k***file_name* **.snk**   
  
     範例： **sn /k ErrorHandling.snk**  
  
     確認訊息，**金鑰組寫入** \< *file_name*\>**.snk** `,`會出現在命令列。  
  
3.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下專案，然後按一下**屬性**。  
  
4.  按一下**簽署**索引標籤，選擇**瀏覽**中**選擇強式名稱金鑰檔**下拉式方塊。  
  
5.  瀏覽至金鑰檔，然後按一下它。 按一下**開啟**，然後關閉 專案屬性。  
  
6.  針對您想要使用此強式名稱組件金鑰檔案部署方案中的每個專案重複步驟 3 到 6。  
  
## <a name="see-also"></a>請參閱  
 [從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)