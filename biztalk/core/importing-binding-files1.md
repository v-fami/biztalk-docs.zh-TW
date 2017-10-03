---
title: "匯入繫結 Files1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- CLASSPATH environment variable
- importing binding files
- cleaning target computer
ms.assetid: b2a9b19b-2d3d-45ea-bd92-a2501791b86a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12fca64580b692f01834b48085aa2d88085fb743
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a>匯入繫結檔案
使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯入繫結檔案之前，請確認下列項目：  
  
-   CLASSPATH 指向 PeopleSoft 專屬檔案的特定位置。 確認這些檔案的位置在新電腦上相同，或編輯繫結檔案。  
  
-   在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。  
  
-   PeopleSoft Enterprise 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。 如需詳細資訊，請參閱[部署限制](../core/deployment-limitations3.md)。  
  
> [!NOTE]
>  部署會覆寫接收位置組態。 當您在目標電腦上部署繫結檔案和組件，在匯入 XML 繫結檔案時，傳送埠和接收位置會遭取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
 如需有關匯入繫結檔案的逐步指示，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜如何將繫結匯入 BizTalk 群組＞主題。  
  
## <a name="cleaning-the-target-computer"></a>清除目標電腦  
 請遵循下列步驟清除目標電腦，以部署新應用程式。  
  
#### <a name="to-clean-the-target-computer"></a>若要清除目標電腦  
  
-   移除協調流程所繫結的傳送埠和接收位置。  
  
     如果目標電腦上尚未安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以執行下列指令碼來移除連接埠：  
  
     **\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs**  
  
     **\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs**  
  
     例如，在命令提示字元下執行：  
  
     **cscript RemoveSendPort.vbs\<傳送埠名稱 >**  
  
## <a name="see-also"></a>另請參閱  
 [部署連接埠和組件](../core/deploying-ports-and-assemblies5.md)