---
title: 如何列出分支機構應用程式的屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fac15775-39d0-470e-b9d2-21b2d02e1de7
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: e35f1f068f63d4db9738733bcada55047e81a19a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250954"
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a>如何列出分支機構應用程式的屬性
**Displayapp**命令顯示分支機構應用程式的下列資訊。 如需分支機構應用程式屬性的詳細資訊，請參閱[SSO 分支機構應用程式](../esso/sso-affiliate-applications.md)。  
  
 單一登入 (SSO) 系統會從您用來更新分支機構應用程式的 XML 檔案中取得這項資訊。 如需詳細資訊，請參閱[如何更新分支機構應用程式的內容](../esso/how-to-update-the-properties-of-an-affiliate-application.md)。  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a>使用管理公用程式顯示分支機構應用程式的屬性  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –displayapp <application name>`，其中*\<應用程式名稱 >* 是您想要顯示的屬性的分支機構應用程式的名稱。  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a>使用用戶端公用程式顯示分支機構應用程式的屬性  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是\<*安裝磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssoclient –displayapp <application name>`，其中*\<應用程式名稱 >* 是您想要顯示的屬性的分支機構應用程式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [管理使用者對應](../esso/managing-user-mappings.md)   
 [管理分支機構應用程式](../esso/managing-affiliate-applications.md)