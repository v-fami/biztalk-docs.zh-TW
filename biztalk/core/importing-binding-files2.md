---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: db28e1db8a0f2d4149e0539e2bce195cd91b1279
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973983"
---
# <a name="importing-binding-files"></a>匯入繫結檔案
本節提供有關部署 BizTalk Adapter for JD Edwards EnterpriseOne 時之匯入程序的資訊。 當您在目標電腦上重新部署繫結檔案 (和組件)，傳送埠和接收位置會在重新匯入 XML 繫結檔案時，被取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
### <a name="to-clean-the-target-computer"></a>若要清除目標電腦  
  
- 移除協調流程所繫結的傳送埠和接收位置。  
  
   如果目標電腦上未安裝 Visual Studio，您可以執行下列指令碼來移除連接埠：  
  
   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\  
  
   Remove Send Port\VBScript\RemoveSendPort.vbs  
  
   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\  
  
   Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
   例如，在命令提示字元下執行：  
  
   **cscript RemoveSendPort.vbs\<傳送埠名稱\>**  
  
## <a name="see-also"></a>另請參閱  
 [匯入 JD Edwards EnterpriseOne 應用程式](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)