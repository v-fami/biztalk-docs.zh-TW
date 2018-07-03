---
title: 匯入 BizTalk 配接器適用於 JD Edwards OneWorld |Microsoft Docs
description: 匯入應用程式的繫結檔案，並檢閱 JD Edwards OneWorld 配接器在 BizTalk 中的任何限制
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f308d2fe-39dd-4008-94ed-292c4c26fe06
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ca65c71e14d488b264d861616fe170220ac249b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999215"
---
# <a name="import-the-jd-edwards-enterpriseone-application"></a>匯入 JD Edwards EnterpriseOne 應用程式
  
## <a name="overview"></a>概觀
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。 BizTalk Server 會將傳送埠/接收位置組態匯出到 XML 檔案。  
  
 您可以使用 BizTalk Server 執行以下工作：  
  
-   在 BizTalk 組態資料庫中部署或移除 BizTalk Server 組件  
  
-   在全域組件快取 (GAC) 中安裝或解除安裝組件  
  
-   將 BizTalk Server 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出  

若要使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]若要將連接埠和組件的部署，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。  
  
> [!NOTE]
>  Microsoft BizTalk Adapter for JD Edwards OneWorld 只要求來源 (部署) 電腦上必須有 Visual Studio； 實際執行電腦上不需要有 Visual Studio。  

## <a name="confirm-your-setup"></a>確認您的設定
使用 BizTalk Server 匯入繫結檔案之前，請確認下列項目：  
  
-   CLASSPATH 指向 JD Edwards 專屬檔案的特定位置。 確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。  
  
-   在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。  
  
-   JD Edwards 系統密碼 (如果出現在組態中) 會以 ***** 格式儲存在繫結檔案中。 請參閱**限制**本主題中。

  
> [!NOTE]
>  部署會覆寫接收位置組態。 在目標電腦上部署繫結檔案 (和組件) 時，傳送埠和接收位置會在匯入時被取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
  
## <a name="clean-the-target-computer"></a>清除目標電腦
部署會覆寫接收位置組態。 當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。  
  
在匯入之前，移除傳送埠和接收位置繫結至協調流程。  
  
如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
例如，在命令提示字元下執行：  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
  
## <a name="limitations"></a>限制
傳輸配接器 」 密碼會儲存為星號 (\*\*\*\*\*\*) 中的繫結檔案匯出 BizTalk 部署精靈 」，並傳遞給管理在相同的格式中的元件。 繫結檔案前先行編輯匯入的星號取代成隨機英數字元值 （也就是不正確的密碼）。 然後輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。  
  
 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。  
  
> [!NOTE]
>  匯入到.msi 檔案時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含企業配接器之繫結資訊的應用程式可能會收到匯入錯誤訊息。 支援的 hotfix 可從 Microsoft 以及在錯誤的完整描述[ http://support.microsoft.com/kb/923733/en-us ](http://support.microsoft.com/kb/923733/en-us)。  
  
### <a name="work-around-the-password-limitation"></a>解決密碼限制問題  

**選項 1**  

- 您匯入之前，更新繫結檔案，並以純文字取代星號。  
  
    > [!CAUTION]
    >  基於安全理由，並不建議使用這個做法。  
  
- 在匯入之前，更新繫結檔案星號取代為某些垃圾值 （也就是不正確的密碼）。 您匯入之後，請輸入正確的密碼使用**傳輸屬性**。  
  
    > [!NOTE]
    >  只有當目標電腦上安裝了 Microsoft Visual Studio，或您開發自訂工具時，才能使用這項解決方法。  
  
**選項 2**  
  
1.  不使用密碼，改為使用「企業單一登入」。 使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。  
  
2.  驗證邏輯系統以及「傳輸」和「接收」服務。  

## <a name="next-steps"></a>後續的步驟
[使用 協調流程中的 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling1.md)