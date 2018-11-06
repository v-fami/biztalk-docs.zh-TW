---
title: 匯入 JD Edwards EnterpriseOne 應用程式 |Microsoft Docs
description: 確認設定，匯入應用程式繫結檔案，然後檢閱 JD Edwards EnterpriseOne 配接器在 BizTalk 中的限制
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 852f948b-48ba-4ae2-b1eb-7c88c1542a52
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9c6f24ff4cb7060d0cddf29d82f4035d8407dca
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50753190"
---
# <a name="import-the-jd-edwards-enterpriseone-application"></a>匯入 JD Edwards EnterpriseOne 應用程式
  
## <a name="overview"></a>總覽
使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以複製連接埠和組件的目標電腦上。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送埠/接收位置將組態匯出到 XML 檔案。  
  
 您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：  
  
- 在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件  
  
- 在全域組件快取 (GAC) 中安裝或解除安裝組件  
  
- 將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件繫結資訊匯入到繫結檔案，或是將之從繫結檔案中匯出  
  
若要使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]若要將連接埠和組件的部署，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。  
  
> [!NOTE]
>  Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 只要求來源 (程式開發) 電腦上必須有 Visual Studio； 實際執行電腦上不需要有 Visual Studio。  

## <a name="confirm-your-setup"></a>確認您的設定
使用 BizTalk Server 匯入繫結檔案之前，必須確認下列項目：  
  
-   CLASSPATH 指向 JD Edwards EnterpriseOne 專屬檔案的特定位置。 確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。  
  
-   在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。  
  
-   JD Edwards EnterpriseOne 系統密碼，如果出現在組態中，會儲存成\* \* \* \* \*繫結檔案中。 如需詳細資訊，請參閱 <<c0>  **限制**本主題中。

## <a name="clean-the-target-computer"></a>清除目標電腦
當您在目標電腦上重新部署繫結檔案 (和組件)，傳送埠和接收位置會在重新匯入 XML 繫結檔案時，被取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
在匯入之前，移除傳送埠和接收位置繫結至協調流程。 如果目標電腦上未安裝 Visual Studio，您可以執行下列指令碼來移除連接埠：  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  

例如，在命令提示字元下執行：  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
## <a name="limitations"></a>限制
傳輸配接器 」 密碼會儲存為星號 (\*\*\*\*\*\*) 繫結檔案所匯出[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，並且會傳遞給管理元件中相同的格式。 在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。  
  
 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。  
  
 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。  
  
### <a name="work-around-the-password-limitation"></a>解決密碼限制問題  
  
1.  不使用密碼，改為使用「企業單一登入」。 使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。  
  
2.  驗證邏輯系統以及「傳輸」和「接收」服務。  


## <a name="next-steps"></a>後續步驟
[使用 協調流程中的 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling3.md)