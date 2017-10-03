---
title: "部署 Limitations4 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, deployment limitations
- deployment, limitations
ms.assetid: 1312627e-9de2-461e-a8c4-66a9d41bb714
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2d8e33c7274ab0f95c6d7fff1bf9746ac86e420
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a>部署限制
「傳輸配接器」密碼以星號 (******) 儲存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯出的繫結檔案中，並且會以相同格式傳遞給管理元件。 在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。  
  
 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。  
  
 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。  
  
> [!NOTE]
>  將包含企業配接器之繫結資訊的 .msi 檔案匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式時，可能會收到匯入錯誤訊息。 支援的 hotfix 可從 Microsoft 以及在錯誤的完整說明[http://go.microsoft.com/fwlink/?LinkId=196087](http://go.microsoft.com/fwlink/?LinkId=196087)。  
  
## <a name="password-limitation-workaround"></a>密碼限制解決方法  
 若要解決密碼限制問題，您可以執行下列程式碼。  
  
#### <a name="to-work-around-the-password-limitation"></a>解決密碼限制問題  
  
1.  不使用密碼，改為使用「企業單一登入」。 使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。  
  
2.  驗證邏輯系統以及「傳輸」和「接收」服務。  
  
## <a name="see-also"></a>另請參閱  
 [部署連接埠和組件](../core/deploying-ports-and-assemblies3.md)