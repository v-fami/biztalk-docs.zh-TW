---
title: "部署 Limitations2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deployment, limitations
- passwords, adapter limitations
ms.assetid: 9db2ca70-5db2-4b14-a898-13049737c188
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05fa9704823bd7e9df9f0bc7d4516719a8a490e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a>部署限制
傳輸配接器 」 密碼會儲存為星號 (\*\*\*\*\*\*) 中繫結檔案匯出 BizTalk 部署精靈 」，並傳遞給管理以相同格式的元件。 匯入星號取代成隨機英數字元值 （也就是不正確的密碼） 之前編輯繫結檔案。 然後輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。  
  
 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。  
  
> [!NOTE]
>  匯入到.msi 檔案時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含企業配接器之繫結資訊的應用程式可能會收到匯入錯誤訊息。 支援的 hotfix 可從 Microsoft 以及在錯誤的完整說明[http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us)。  
  
## <a name="password-limitation-workaround"></a>密碼限制解決方法  
 使用下列其中一種解決方法的密碼限制問題。  
  
#### <a name="to-work-around-the-password-limitation"></a>解決密碼限制問題  
  
1.  在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。  
  
    > [!CAUTION]
    >  基於安全理由，並不建議使用這個做法。  
  
2.  在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。 輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。  
  
    > [!NOTE]
    >  只有當目標電腦上安裝了 Microsoft Visual Studio，或您開發自訂工具時，才能使用這項解決方法。  
  
 **-或-**  
  
#### <a name="to-work-around-the-password-limitation"></a>解決密碼限制問題  
  
1.  不使用密碼，改為使用「企業單一登入」。  
  
     使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。  
  
2.  驗證邏輯系統以及「傳輸」和「接收」服務。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 JD Edwards OneWorld 傳輸屬性](../core/how-to-set-jd-edwards-oneworld-transport-properties.md)   
 [部署連接埠和組件](../core/deploying-ports-and-assemblies4.md)