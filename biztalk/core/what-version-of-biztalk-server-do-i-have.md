---
title: 是否有哪個版本的 BizTalk Server？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb651202-f682-4e5f-8a79-221877af20a7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7003f2d3c61345462ca484f627110a6e507e748
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976975"
---
# <a name="what-version-of-biztalk-server-do-i-have"></a>是否有哪個版本的 BizTalk Server？
您可能執行不同版本和不同版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 本主題會示範如何判斷[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝資訊，包括版本號碼、 版本，以及安裝路徑。  

## <a name="use-the-registry"></a>使用登錄

1. 選取 **開始**，型別`regedt32`，然後再開啟它。  

2. 依序展開**HKEY_LOCAL_MACHINE**，展開**軟體**，展開**Microsoft**，展開**BizTalk Server**，然後選取  **3.0**。  

3. 右窗格會顯示安裝的詳細資訊，包括：  


   |      子機碼       |                                                                                                         描述                                                                                                          |
   |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  **InstallPath**   |                                             列出已安裝的安裝路徑[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。                                              |
   | **Productedition 無效** |                                                        列出版本，包括：<br /><br /> 開發人員<br />分支機構<br />標準<br />-Enterprise                                                         |
   | **ProductVersion** | 列出的基底的產品版本。 如需特定產品版本，包括 service pack 和累計更新，請參閱[BizTalk 版本](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx)。 |

## <a name="use-the-control-panel"></a>使用控制台

1.  選取 **開始**，型別`Programs and Features`，然後再開啟它。  

2. 在清單中，選取**Microsoft BizTalk Server**。 列出的版本。

請參閱[BizTalk 版本](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx)。

## <a name="see-also"></a>另請參閱  
 [開始使用](../core/getting-started-with-biztalk-server.md)