---
title: 部署 BizTalk 應用程式的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, deploying
- best practices, applications
- applications, best practices
- deploying, best practices
ms.assetid: 97ebf479-0dc5-4e95-b409-d3b6ad3d60d0
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3b50ff0a6e64633090e562b6ca8e3ae66eb8683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233062"
---
# <a name="best-practices-for-deploying-a-biztalk-application"></a>部署 BizTalk 應用程式的最佳作法
本主題說明部署 BizTalk 應用程式的最佳作法。  
  
## <a name="group-related-artifacts-together-in-a-single-application"></a>將相關的成品分組到單一應用程式  
 盡可能將相關的成品放置在相同的 BizTalk 應用程式中。 這可讓您將成品做為單一實體管理和部署，讓管理變的更容易。 您可將支援相同商務程序或執行類似功能的成品分組到單一應用程式。  
  
## <a name="deploy-shared-artifacts-in-a-separate-application"></a>將共用的成品部署到個別的應用程式  
 如果成品將由兩個以上的應用程式共用，請將共用的成品部署到個別的應用程式。 例如，如果兩個應用程式共用某結構描述，請將該結構描述放置到個別的應用程式中。 這是因為 BizTalk 群組中只能存在一個具有相同本機唯一識別碼 (LUID) 的成品，此識別碼是由成品名稱以及選擇性的其他屬性所組成。 如果您將成品包含在一個應用程式中，然後從另一個應用程式建立其參考，可能會遇到一些問題，例如在停止包含該成品的應用程式時，參考的應用程式便無法正確運作。  
  
 這個最佳方法適用於所有成品類型，除了檔案之外，例如讀我檔案和指令碼，它們會做為成品的檔案類型新增至應用程式。 這是因為在 BizTalk 群組中可部署一個以上具有相同名稱的檔案成品。 因此，您可使用在兩個以上的應用程式中具有相同名稱的檔案。 停止一個應用程式不會影響另一個應用程式。 如需有關如何新增檔案成品的詳細資訊，請參閱[如何將檔案新增至應用程式](../core/how-to-add-a-file-to-an-application.md)。  
  
 如需共用特定成品類型的最佳作法，請參閱本節中的＜將共用的網站部署到個別的應用程式＞、＜將共用的原則部署到個別的應用程式＞及＜將共用的憑證部署到個別的應用程式＞。  
  
## <a name="deploy-a-shared-web-site-in-a-separate-application"></a>將共用的網站部署到個別的應用程式  
 如果網站將由一個以上的商務方案共用，請將網站部署到個別的應用程式。 這是因為當您解除安裝 BizTalk 應用程式時，任何屬於該應用程式的網站虛擬目錄都會被移除，即使該網站正在執行中也一樣。 如果另一個商務方案共用該網站，則其他商務方案將無法再正常運作。  
  
## <a name="deploy-shared-policies-in-a-separate-application"></a>將共用的原則部署到個別的應用程式  
 如果兩個以上的應用程式使用一個原則，您應該將其部署到個別的應用程式，而不要從一個應用程式建立對另一個應用程式的參考。 這是因為當您停止應用程式時，其原則也會被解除部署。 如果您停止的應用程式中包含另一個應用程式使用的原則，該原則在兩個應用程式都將無法再運作。  
  
## <a name="deploy-shared-certificates-in-a-separate-application"></a>將共用的憑證部署到個別的應用程式  
 如果憑證由兩個以上之應用程式中的傳送埠或接收位置使用，您應該將該憑證部署到個別的應用程式中，然後從需要使用該憑證的應用程式參考此應用程式。 這是因為 BizTalk 群組中只能存在一個具有特定 LUID 的成品，所以您將無法在兩個不同的應用程式中匯入相同的憑證。 如果您嘗試匯入使用相同憑證的兩個應用程式，第一個匯入會成功，第二個匯入則會失敗。 在此情況下，使用覆寫匯入選項無法修正此問題，因為您想要覆寫的現有憑證包含在另一個應用程式中。  
  
## <a name="never-deploy-an-assembly-from-visual-studio-on-a-production-computer"></a>絕對不要在實際執行電腦上從 Visual Studio 部署組件  
 在開發過程中，開發人員通常必須從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 重新部署組件。 為了重新部署，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 可以解除部署、解除繫結、停止及取消登錄組件中包含的成品。 雖然這在開發環境中是必要且適當的動作，但卻可能在實際執行環境中造成無法預期的嚴重後果。 基於這個理由，以及避免任何人嘗試在實際執行電腦上從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 部署組件的可能性，我們建議您絕對不要在實際執行電腦上安裝 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
 此外，也絕對不要從執行 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的電腦參考實際執行資料庫。  
  
## <a name="when-deploying-large-msi-files-you-may-need-to-increase-the-default-transaction-timeout-of-the-com-components-used-by-biztalk-to-deploy-applications"></a>在部署大型 MSI 檔案時，您可能需要增加 BizTalk 用來部署應用程式的 COM+ 元件預設交易逾時。  
 如果正在部署的 MSI 檔案非常大 (超過 100 MB)，則應用程式可能無法在 BizTalk 在應用程式部署期間所使用的 COM+ 元件預設交易逾時內完成部署。 如果在部署完成之前，與這些 COM+ 元件關聯的交易逾時，部署將會失敗。 如果您正在部署非常大的 MSI 檔案，可考慮使用下列其中一個方式減輕這個問題：  
  
1.  部署數個較小的 MSI 檔案取代一個大型 MSI 檔案。  
  
2.  增加與關聯的 3000 秒預設交易逾時**元件服務**和**Microsoft.biztalk.applicationdeployment.group**中的元件**元件服務**管理介面。 這些元件屬於**Microsoft.BizTalk.ApplicationDeployment.Engine**和**Microsoft.Biztalk.Deployment** COM + 應用程式分別。 如需有關如何變更交易逾時值的 COM + 元件請參閱[如何變更 MTS 或 COM + 交易逾時值](http://go.microsoft.com/fwlink/?LinkId=67691)。  
  
## <a name="see-also"></a>另請參閱  
 [部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)