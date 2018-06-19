---
title: 部署應用程式的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e5fb4f6-f9bd-4322-93f9-723e9e3c3317
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7fa139469ea8718c3d4430235ffb576195e67a7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008231"
---
# <a name="known-issues-with-deploying-an-application"></a>部署應用程式的已知的問題
## <a name="deploying-a-biztalk-application"></a>部署 BizTalk 應用程式  
 **部署更新的應用程式需要修正的參考**  
  
 如果要部署全新的應用程式以取代現有的應用程式，則必須修改其他應用程式與您要取代之應用程式間的所有參考。  
  
 **使用 Visual Studio 來部署應用程式可以停止應用程式**  
  
> [!NOTE]  
>  我們建議您避免使用 Visual Studio 部署到生產環境應用程式。  
  
 如果您使用 Visual Studio 部署到生產環境應用程式並重新啟動主控件執行個體選項是當您部署應用程式，包括未與相關聯時，將會重新啟動設為 True，在專案屬性中，所有的主控件執行個體此應用程式。 這樣會停止在本機電腦的任何主控件執行個體上執行的所有其他應用程式。  
  
## <a name="adding-artifacts-to-a-biztalk-application"></a>將成品新增至 BizTalk 應用程式  
 **移動成品可以移動相依性**  
  
 當您將成品移到新的應用程式時，在其有相依性的其他任何成品也會移除非新的應用程式有某個參照指向已移動的成品相依成品的應用程式。 此外，相依於移動之成品的任何成品也會移動，除非包含這些成品的應用程式有參考新的應用程式。 當您移動成品時，系統會為您顯示也將一併移動之其他成品的清單。 如需移動成品的指示，請參閱[如何將成品移至不同的應用程式](http://go.microsoft.com/fwlink/?LinkId=154999)(http://go.microsoft.com/fwlink/?LinkId=154999)。  
  
## <a name="exporting-a-biztalk-application"></a>匯出 BizTalk 應用程式  
 **安裝 Windows Vista 上的.msi 檔案時，就可以顯示不正確的錯誤**  
  
 當安裝.msi 封裝使用匯出[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]Windows Vista® 上執行的 BizTalk Server，您可能會收到下列不正確的錯誤，「 安裝程式發現未預期的錯誤，安裝此套件。 這可能表示封裝有問題。 錯誤碼是 2869」。 若要更正這個錯誤，第一次匯入封裝使用 BizTalk Server，然後重新匯出並安裝套件。  
  
## <a name="importing-a-biztalk-application"></a>匯入 BizTalk 應用程式  
 **密碼不會移除從繫結檔案新增至應用程式**  
  
 基於安全性考量，應用程式匯出期間將從應用程式繫結移除密碼。 但是，並不是從新增至應用程式的繫結檔案中移除密碼。 匯入應用程式後，您必須重新設定密碼，應用程式才能正常運作。 您可以藉由編輯繫結檔案，或使用管理主控台。 如需有關編輯繫結檔案的詳細資訊，請參閱[自訂繫結檔案](http://go.microsoft.com/fwlink/?LinkId=155000)(http://go.microsoft.com/fwlink/?LinkId=155000)。 如需設定配接器安全性的詳細資訊，請參閱[使用配接器](http://go.microsoft.com/fwlink/?LinkId=155001)(http://go.microsoft.com/fwlink/?LinkId=155001)。  
  
 **BizTalk Server 不會回復已編寫指令碼匯入或安裝**  
  
 當匯入作業失敗時，除了自訂指令碼執行的動作外，BizTalk Server 會回復所有的匯入作業。 這也適用於安裝和解除安裝作業。  
  
 **遺漏的結構描述可能不會報告匯入之後**  
  
 如果您在一個使用其他應用程式中之屬性結構描述的應用程式內建立傳送埠的篩選，然後再將此應用程式匯入至新的 BizTalk 群組，那麼您在安裝及啟動應用程式時，將不會收到結構描述遺失的警告，並且篩選功能也無法運作。 在安裝沒有包含結構描述的應用程式之前，您可以先匯入包含結構描述的應用程式來修正問題。  
  
## <a name="see-also"></a>請參閱  
 [部署應用程式](../technical-guides/deploying-an-application.md)