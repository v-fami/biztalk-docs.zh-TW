---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 907c21377a6affd5a99576137a5babaa1626c135
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971300"
---
# <a name="import-binding-files"></a>匯入繫結檔案

## <a name="overview"></a>概觀
使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯入繫結檔案之前，請確認下列項目：  
  
-   CLASSPATH 指向 PeopleSoft 專屬檔案的特定位置。 確認這些檔案的位置在新電腦上相同，或編輯繫結檔案。  
  
-   在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。  
  
-   PeopleSoft Enterprise 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。 
  
> [!NOTE]
>  部署會覆寫接收位置組態。 當您在目標電腦上部署繫結檔案和組件，在匯入 XML 繫結檔案時，傳送埠和接收位置會遭取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
 如需有關匯入繫結檔案的逐步指示，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜如何將繫結匯入 BizTalk 群組＞主題。  
  
## <a name="clean-the-target-computer"></a>清除目標電腦  
若要清除目標電腦，部署新的應用程式、 移除傳送埠和接收位置繫結至協調流程。  
  
如果目標電腦上尚未安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以執行下列指令碼來移除連接埠：  
  
**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs**  
  
**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs**  
  
例如，在命令提示字元下執行：  
  
**cscript RemoveSendPort.vbs\<傳送埠名稱\>**  
  
