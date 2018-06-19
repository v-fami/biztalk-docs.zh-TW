---
title: 匯入繫結 for TIBCO EMS |Microsoft 文件
description: 部署您的 BizTalk 配接器在 BizTalk Server 中使用匯入繫結功能的 TIBCO Enterprise Message Service 應用程式
ms.custom: ''
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69dae448-4ec6-4a56-a628-bb447bc21b62
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79f7f3ec0478746b8c2c6762fe212229f9c7b11d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25969398"
---
# <a name="deploy-tibco-ems-ports-and-assemblies"></a>部署 TIBCO EMS 通訊埠和組件

## <a name="overview"></a>概觀
與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以複製連接埠和組件的目標電腦上。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯出至 XML 檔案傳送埠/接收位置組態。  
  
 您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：  
  
-   在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件。  
  
-   在全域組件快取 (GAC) 中安裝或解除安裝組件。  
  
-   將 BizTalk 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。  
  
 如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。  
  
> [!NOTE]
>  Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 只要求來源 (開發) 電腦上必須有 Visual Studio； 實際執行電腦上不需要有 Visual Studio。  

## <a name="confirm-your-setup"></a>確認您的設定
使用 BizTalk Server 匯入繫結檔案之前，請確認下列項目：  
  
-   在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。  
  
-   TIBCO Enterprise Message Service 系統密碼 (如果出現在組態中) 必須以 ***** 格式儲存在繫結檔案中。 請參閱**限制**本主題中。


## <a name="clean-the-target-computer"></a>清除目標電腦
部署會覆寫接收位置組態。 當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。  

在匯入之前，移除任何傳送埠和接收位置繫結至協調流程。  
  
如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：  
  
`\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs`  
  
`\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs`
  

例如，在命令提示字元下執行：  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```

## <a name="limitations"></a>限制
傳輸配接器密碼會儲存為顆星 (\*\*\*\*\*\*) 繫結檔案中，會匯出 BizTalk Server 中，並且會傳遞給管理元件相同的格式。 在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。 輸入正確的密碼使用 **傳輸屬性** 匯入繫結檔案後在 BizTalk Server 管理主控台中的頁面。  
  
 此為已知的限制狀況。 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。  
  
 
### <a name="password-limitation-workaround"></a>密碼限制解決方法  
 若要解決這項密碼限制問題，請使用下列其中一個方法：  
  
-   在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。  
  
    > [!CAUTION]
    >  基於安全理由，並不建議使用這個做法。  
  
-   在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。 輸入正確的密碼使用 **傳輸屬性** 匯入繫結檔案後在 BizTalk Server 管理主控台中的頁面。  
  
    > [!NOTE]
    >  只有當目標電腦上安裝了 Visual Studio，或您開發自訂工具時，才能使用這項解決方法。  
  
-   驗證邏輯系統以及「傳輸」和「接收」服務。  

## <a name="next-steps"></a>後續的步驟
[在您的協調流程中使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling5.md)