---
title: 如何重新整理資源 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [resources], refreshing
- refreshing resources
- resources, refreshing
ms.assetid: d6ff7c9d-8aaf-42a4-b1a3-00c05f6ac869
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bee05b9f137bbec92eccfa217084b66f1e5bf8ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254542"
---
# <a name="how-to-refresh-a-resource"></a>如何重新整理資源
本主題描述如何使用 BizTalk Server 管理主控台來重新整理資源成品。 此作業會更新 BizTalk 管理資料庫中的成品資訊。 若要這樣做的另一個方法是將成品新增至應用程式使用 BTSTask [AddResource 命令](../core/addresource-command.md)與覆寫選項。  
  
 資源成品包含在應用程式的 [資源] 資料夾中。 如果您變更了來源檔案，而且想要以更新過的檔案取代應用程式中的檔案，您可能需要重新整理資源成品。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-refresh-a-resource-artifact"></a>若要重新整理資源成品  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組包含資源成品重新整理，然後展開包含該成品的應用程式。  
  
3.  按一下**資源**資料夾、 以滑鼠右鍵按一下要重新整理檔案，然後按一下**修改**。  
  
4.  在**修改資源**對話方塊、 選取要重新整理檔案，然後按一下**重新整理**。  
  
5.  瀏覽至您要取代目前的檔案更新的檔案，然後按一下**確定**。  
  
     目前的檔案隨即取代成更新的檔案。 在加入、 設定、 設定顯示在**選項** 索引標籤**修改資源**對話方塊會套用到的重新整理的檔案。 如需有關如何變更這些設定的詳細資訊，請按一下**協助**在對話方塊中。  
  
## <a name="see-also"></a>另請參閱  
 [管理前置或後置處理指令碼](../core/managing-pre-and-post-processing-scripts.md)   
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [管理資源](../core/managing-resources.md)