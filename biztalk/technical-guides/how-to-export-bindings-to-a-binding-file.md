---
title: 如何將繫結匯出至繫結檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3734ae6d-b790-40f2-8403-d7c7fdbe381b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ab9dd60b37c16169f76e052706adb43c4606fcf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982215"
---
# <a name="how-to-export-bindings-to-a-binding-file"></a>如何將繫結匯出至繫結檔案
您可以匯出至另一個現有 BizTalk 應用程式使用的繫結檔案的 BizTalk 應用程式的繫結。 您也可以匯出群組中的所有繫結或組件的繫結。 接著，您可以將這些繫結匯入到應用程式或群組。  
  
 繫結檔案是 XML 檔案，描述 BizTalk 管理資料庫和其關聯性中的成品。 它包含每個 BizTalk Server 協調流程、 管線、 對應或結構描述範圍內的 BizTalk 組件、 應用程式或群組的繫結資訊。 它包含每個傳送埠的組態設定、 傳送埠群組、 接收埠、 接收位置和合作對象。 此外，它也會描述每個協調流程繫結至的主機和其信任層級。  
  
## <a name="why-to-export-to-a-binding-file"></a>若要匯出至繫結檔案的原因  
 繫結檔案可加速部署在下列情況下不需要手動設定繫結：  
  
- **將應用程式從一個部署環境移至另一個**  
  
   使用繫結檔案可加快部署速度所避免需要手動設定不同的部署環境的繫結這類從開發環境至測試環境。  
  
- **更新組件**  
  
   您可以使用繫結檔案會自動套用或重新套用至組件的更新後的組件的繫結。  
  
- **將組件部署到多個 BizTalk 群組**  
  
   您可以避免需要個別設定使用繫結檔案部署到多個 BizTalk 群組的組件的繫結。  
  
  使用繫結檔案可讓您將繫結套用至應用程式的彈性。 當您匯出至.msi 檔案的應用程式時，您只能指定所有的應用程式的繫結會匯出至.msi 檔案。 您可以使用繫結檔案執行下列作業：  
  
- 從目前的應用程式的所有繫結，所有的繫結，從目前的群組或只有單一組件的繫結，請匯出至繫結檔案。 （您可以使用這樣的匯出繫結命令 [管理] 主控台中的應用程式。）  
  
- 如此會立即套用其繫結，或讓應用程式匯入另一個群組時，會套用繫結，您可以繫結檔案新增至應用程式 （使用 [新增資源] 命令）。  
  
- 您可以將多個繫結檔案新增至應用程式 （使用 [新增資源] 命令），並指定每個目標部署環境。 這可讓您針對多個部署環境使用單一的部署套件。 當您匯入應用程式時，您可以選取要套用的繫結。  
  
- 您可以匯出個別的繫結檔案的應用程式中的多個組件。  
  
- 在產生繫結檔後，您依然能夠加以編輯以變更其繫結資訊。  
  
## <a name="how-to-export-to-a-binding-file"></a>如何匯出至繫結檔案  
 在 BizTalk Server 管理主控台中，執行應用程式匯出繫結命令或命令列上使用 BTSTask ExportBindings 命令，您可以匯出繫結檔案的應用程式的繫結。  
  
 基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。  
  
 繫結檔案中的資訊會取代現有的組態資訊。 如果繫結檔案中的成品名稱與現有組態中的成品名稱相符，則當您匯入繫結檔案時，繫結檔案中的成品將會更新現有組態中的成品。  
  
 如需如何儲存在繫結檔案的主機和信任層級，繫結檔案中的主控件和信任層級如何比對主機和信任層級中應用程式，並套用繫結的順序，請參閱[繫結檔案和應用程式部署](http://go.microsoft.com/fwlink/?LinkID=154726)(http://go.microsoft.com/fwlink/?LinkID=154726)。 如需有關如何匯出 BizTalk 應用程式的繫結的指示，請參閱 <<c0> [ 如何匯出 BizTalk 應用程式的繫結](http://go.microsoft.com/fwlink/?LinkId=155009)(http://go.microsoft.com/fwlink/?LinkId=155009)。