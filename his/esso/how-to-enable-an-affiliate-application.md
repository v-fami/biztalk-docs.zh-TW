---
title: 如何啟用分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 051bc35f-55e6-4811-9559-b1bb66a570ce
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 53dcd9886bc808f84b112146971a6f9519c404e2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250930"
---
# <a name="how-to-enable-an-affiliate-application"></a>如何啟用分支機構應用程式
您可以使用 MMC 嵌入式管理單元或**enableapp**命令以啟用指定的分支機構應用程式。  
  
### <a name="to-enable-an-affiliate-application-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元啟用分支機構應用程式  
  
1.  按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下分支機構應用程式，然後按一下 **啟用**。  
  
### <a name="to-enable-an-affiliate-application-using-the-command-line"></a>若要啟用分支機構應用程式使用命令列  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –enableapp <application name>`，其中\<*應用程式名稱*> 是您想要啟用分支機構應用程式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../esso/sso-affiliate-applications.md)   
 [如何建立分支機構應用程式](../esso/how-to-create-an-affiliate-application.md)   
 [管理使用者對應](../esso/managing-user-mappings.md)   
 [管理分支機構應用程式](../esso/managing-affiliate-applications.md)