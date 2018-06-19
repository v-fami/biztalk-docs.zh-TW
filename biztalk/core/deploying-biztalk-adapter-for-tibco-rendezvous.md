---
title: 匯入繫結的 TIBCO Rendezvous |Microsoft 文件
description: 部署您的 BizTalk Adapter for TIBCO Rendezvous 使用 BizTalk Server 中匯入繫結功能的應用程式
ms.custom: ''
ms.date: 10/24/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec5751a9-0a08-4cf8-a3ef-e51e488a4180
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dab62d7d7836a59c66329c2c58f7768bc481c036
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968484"
---
# <a name="deploy-tibco-rendezvous-ports-and-assemblies"></a>部署 TIBCO Rendezvous 連接埠和組件
  
## <a name="overview"></a>概觀
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。 精靈會將傳送埠/接收位置組態匯出到 XML 檔案。  
  
 您可以使用 BizTalk Server 執行下列工作：  
  
-   在BizTalk 組態資料庫中部署或移除 BizTalk Server 組件。  
  
-   在全域組件快取 (GAC) 中安裝或解除安裝組件。  
  
-   將 BizTalk Server 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。  
  
 如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。  
  
> [!NOTE]
>  Microsoft BizTalk Adapter for TIBCO Rendezvous 只要求來源 (開發) 電腦上必須有 Visual Studio。 實際執行電腦上不需要有 Visual Studio。  

## <a name="confirm-your-setup"></a>確認您的設定

在使用之前[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]匯入繫結檔案，確認有用於回應的資料夾存在，且它們是否完全相同的新電腦上，或您必須編輯繫結檔案。  
  
## <a name="clean-the-target-computer"></a>清除目標電腦
部署會覆寫接收位置組態。 當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。  
  
在匯入之前，移除傳送埠和接收位置繫結至協調流程。  
  
如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
例如，在命令提示字元下執行：  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
  
## <a name="next-steps"></a>後續的步驟
[在您的協調流程中使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling4.md)  
[疑難排解](../core/troubleshooting-tibco-rendezvous.md)