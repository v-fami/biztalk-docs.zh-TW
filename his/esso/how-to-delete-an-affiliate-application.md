---
title: 如何刪除分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec290d38-0220-4bf2-b596-2d6453e51c8d
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: d0632f7e4217cb9bbccd2ee604688f22eb6de348
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250978"
---
# <a name="how-to-delete-an-affiliate-application"></a>如何刪除分支機構應用程式
使用 MMC 嵌入式管理單元或**deleteapps**認證資料庫中刪除指定的分支機構應用程式的命令。  
  
> [!IMPORTANT]
>  當您刪除分支機構應用程式時，SSO 系統會自動刪除所有與其關聯的對應。  
  
> [!IMPORTANT]
>  您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元刪除分支機構應用程式  
  
1.  按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 範圍 窗格的 MMC 嵌入式管理單元，依序展開 **企業單一登入** 節點。  
  
3.  以滑鼠右鍵按一下分支機構應用程式，然後按一下 **刪除**。  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a>使用命令列刪除分支機構應用程式  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –deleteapp <application name>`，其中*\<應用程式名稱 >* 是您想要移除認證資料庫中的分支機構應用程式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../esso/sso-affiliate-applications.md)   
 [如何啟用分支機構應用程式](../esso/how-to-enable-an-affiliate-application.md)   
 [管理使用者對應](../esso/managing-user-mappings.md)   
 [管理分支機構應用程式](../esso/managing-affiliate-applications.md)