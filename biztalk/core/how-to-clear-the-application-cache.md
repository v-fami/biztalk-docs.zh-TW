---
title: 如何清除應用程式快取 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- caching, applications
- managing [SSO applications], clearing cache
- applications [SSO], caching
ms.assetid: 6230b9a4-c7b8-47b4-854b-12853d9bf5b0
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 106435fafcd9319fcee1df9bdf1b64396fa2006f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973167"
---
# <a name="how-to-clear-the-application-cache"></a>如何清除應用程式快取
您可以使用 MMC 嵌入式管理單元或命令列，移除所有「單一登入伺服器」上特定應用程式的認證快取內容 (所有與分支機構應用程式相關的資訊)。  
  
### <a name="to-clear-the-cache-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元清除快取  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  按一下 **分支機構應用程式**。  
  
4.  在 結果 窗格中，以滑鼠右鍵按一下分支機構應用程式，然後按一下 **清除**。  
  
### <a name="to-clear-the-cache-using-the-command-line"></a>使用命令列清除快取  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 型別<strong>ssomanage-purgecache *\<應用程式名稱\></strong><em>，其中\<</em>應用程式名稱*\>名稱分支機構應用程式，您想要清除的快取。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)