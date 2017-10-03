---
title: "部署 Limitations3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, deployment limitations
- deployment, password limitations
- transport adapter password
ms.assetid: 79cd330f-ecc5-430e-9d79-608593d873cb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae0d01947e0769189c269a1853e7fda0e11cedb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a>部署限制
「傳輸配接器」密碼以星號 (******) 儲存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯出的繫結檔案中，並且會以相同格式傳遞給管理元件。  
  
 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，匯入作業完成後您必須刪除繫結檔案中的密碼。  
  
> [!NOTE]
>  將包含企業配接器之繫結資訊的 .msi 檔案匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式時，可能會收到匯入錯誤訊息。 支援的 hotfix 可從 Microsoft 以及在錯誤的完整說明[http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087)。  
  
## <a name="password-limitation-workaround"></a>密碼限制解決方法  
 若要解決這項密碼限制問題，請使用下列其中一個方法：  
  
-   在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。  
  
    > [!CAUTION]
    >  基於安全性理由，並不建議使用這個做法。  
  
-   在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。 輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。  
  
    > [!NOTE]
    >  只有當目標電腦上安裝了 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，或您開發自訂工具時，才能使用這項解決方法。  
  
 -或-  
  
-   不使用密碼，改為使用「企業單一登入」(SSO)。  
  
     使用 SSO 選項需要先匯入繫結檔案。  
  
 驗證邏輯系統以及「傳輸」和「接收」服務。  
  
## <a name="see-also"></a>另請參閱  
 [部署連接埠和組件](../core/deploying-ports-and-assemblies5.md)