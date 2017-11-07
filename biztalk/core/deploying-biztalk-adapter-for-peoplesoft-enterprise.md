---
title: "PeopleSoft 應用程式匯入 |Microsoft 文件"
description: "您的 PeopleSoft 配接器應用程式匯入到 BizTalk Server 使用 XML 繫結檔案，而讀取的任何限制，當匯入"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f53d1b4-e1df-41ff-b554-1bb1d20b9111
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dad4639c8432b5b9cc61935afadb0703a363045
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="deploy-biztalk-adapter-for-peoplesoft-enterprise"></a>部署 BizTalk Adapter for PeopleSoft Enterprise
本節提供有關部署 BizTalk Adapter for PeopleSoft Enterprise 的詳細資訊。  

## <a name="overview"></a>概觀
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送埠/接收位置將組態匯出成 XML 檔案。  
  
 您會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：  
  
-   在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件。  
  
-   在全域組件快取 (GAC) 中安裝或解除安裝組件。  
  
-   將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。  
  
若要使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。  
  
> [!NOTE]
>  Microsoft BizTalk Adapter for PeopleSoft Enterprise 只要求來源 (開發) 電腦上必須有 Visual Studio。 實際執行電腦上不需要有 Visual Studio。  

## <a name="confirm-your-setup"></a>確認您的設定
使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯入繫結檔案之前，請確認下列項目：  
  
-   CLASSPATH 指向 PeopleSoft 專屬檔案的特定位置。 確認這些檔案的位置在新電腦上相同，或編輯繫結檔案。  
  
-   在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。  
  
-   PeopleSoft Enterprise 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。 請參閱**限制**本主題中。

> [!NOTE]
>  部署會覆寫接收位置組態。 當您在目標電腦上部署繫結檔案和組件，在匯入 XML 繫結檔案時，傳送埠和接收位置會遭取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
 如需有關匯入繫結檔案的逐步指示，請參閱[如何匯入繫結至 BizTalk 群組](../core/how-to-import-bindings-into-a-biztalk-group.md)。 
  
## <a name="clean-the-target-computer"></a>清除目標電腦
若要清除目標電腦，部署新的應用程式、 移除傳送埠和接收位置繫結至協調流程。  
  
如果目標電腦上尚未安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以執行下列指令碼來移除連接埠：  
  
**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs**  
  
**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs**  
  
例如，在命令提示字元下執行：  
  
```
cscript RemoveSendPort.vbs \<Send port name>
```

## <a name="limitations"></a>限制
傳輸配接器 」 密碼以星號 （*） 儲存在繫結檔案匯出的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，並且會傳遞給管理元件，在相同的格式。  
  
 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，匯入作業完成後您必須刪除繫結檔案中的密碼。  
  

### <a name="work-around-the-password-limitation"></a>解決密碼限制問題  

**選項 1**   
  
-   在匯入之前，更新繫結檔案以純文字取代星號。  
  
    > [!CAUTION]
    >  基於安全性理由，並不建議使用這個做法。  
  
-   您匯入之前，先更新星號取代為某些垃圾值 （也就是不正確的密碼） 的繫結 fileby。 您匯入後，請輸入正確的密碼中**傳輸屬性**BizTalk Server 管理 中。  
  
    > [!NOTE]
    >  只有當目標電腦上安裝了 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，或您開發自訂工具時，才能使用這項解決方法。  
  
**選項 2**  
  
-   不使用密碼，改為使用「企業單一登入」(SSO)。 使用 SSO 選項需要先匯入繫結檔案。  
  
- 驗證邏輯系統以及「傳輸」和「接收」服務。 
  
## <a name="next-steps"></a>後續的步驟
[在您的協調流程中使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling2.md)