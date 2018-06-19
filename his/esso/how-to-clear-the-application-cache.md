---
title: 如何清除應用程式快取 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a897791-d32f-46a4-8c5d-2b2161e92bd9
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 24954e8314bc94d4570eb57acbf1d4b03bebb65b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250938"
---
# <a name="how-to-clear-the-application-cache"></a>如何清除應用程式快取
使用 MMC 嵌入式管理單元或**purgecache**命令可移除的認證快取 （所有的資訊與分支機構應用程式相關聯） 的所有單一登入 (SSO) 伺服器上指定的應用程式。  
  
### <a name="to-clear-the-cache-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元清除快取  
  
1.  按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  按一下  **分支機構應用程式**。  
  
4.  在結果窗格中，以滑鼠右鍵按一下分支機構應用程式，然後按一下 **清除**。  
  
### <a name="to-clear-the-cache-using-the-command-line"></a>使用命令列清除快取  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –purgecache <application name>`，其中\<*應用程式名稱*> 是您想要清除的快取的分支機構應用程式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../esso/sso-affiliate-applications.md)   
 [管理分支機構應用程式](../esso/managing-affiliate-applications.md)