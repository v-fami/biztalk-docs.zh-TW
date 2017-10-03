---
title: "是否有 BizTalk Server 的版本？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb651202-f682-4e5f-8a79-221877af20a7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce5508a3b7c78e52fe5fcbef40e351dce58f2816
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-version-of-biztalk-server-do-i-have"></a>是否有 BizTalk Server 的版本？
您可能執行不同版本與不同版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 本主題會示範如何判斷[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝資訊，包括版本號碼、 版本與安裝路徑。  
  
## <a name="use-the-registry"></a>使用登錄
  
1.  選取**啟動**，型別`regedt32`，然後再開啟它。  
  
2.  展開**HKEY_LOCAL_MACHINE**，依序展開**軟體**，依序展開**Microsoft**，依序展開**BizTalk Server**，然後選取  **3.0**。  
  
3.  在右窗格會顯示安裝資訊，包括：  
  
    |子機碼|Description|  
    |--------------|-----------------|  
    |**InstallPath**|列出您安裝的安裝路徑[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。|  
    |**ProductEdition**|列出版本，包括：<br /><br /> 開發人員<br />分支機構<br />標準<br />企業|  
    |**ProductVersion**|列出的基底的產品版本。 如需特定產品版本，包括 service pack 和累計更新，請參閱[BizTalk 版本](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx)。|  

## <a name="use-the-control-panel"></a>使用控制台

1.  選取**啟動**，型別`Programs and Features`，然後再開啟它。  

2. 在清單中，選取**Microsoft BizTalk Server**。 列出的版本與版本。

請參閱[BizTalk 版本](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx)。
  
## <a name="see-also"></a>另請參閱  
 [開始使用](../core/getting-started-with-biztalk-server.md)