---
title: 相依性和應用程式部署 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying [applications], dependencies
- assemblies, dependencies
- artifacts, dependencies
- applications, dependencies
ms.assetid: b78c5a0d-b042-4862-bce7-59469365b369
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cc7e4b44a09da04e62062d90cd99da0354cca34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242206"
---
# <a name="dependencies-and-application-deployment"></a>相依性和應用程式部署
本主題描述兩個或多個 BizTalk 應用程式內成品之間的相依性如何影響應用程式部署和維護。  
  
 當一個成品需要使用另一個成品才能正常運作時，它要*相依*另一個成品。 這類相依性的一個範例，就是當協調流程需要使用特定的結構描述來解析訊息，或是需要使用特定的管線才能正確傳輸訊息時。 在這兩個案例下，此協調流程會相依於另一個成品。  
  
 在您可以更新應用程式中的成品之前，必須先將它解除部署，連同相依於它的任何成品。 當具有相依性的成品存在於相同的應用程式中時，BizTalk Server 會自動針對更新和相依的成品處理解除部署和重新部署工作。 但是，當具有相依性的成品存在於其他應用程式中時，就不是這個情況。 您必須先採取手動步驟來解除部署具有相依性的成品，然後才可以更新這些成品所相依的成品。 之後，您必須以手動方式重新部署相依的成品。  
  
 為了避免在您想要更新其他成品所相依的成品時必須採取這些手動步驟，您可以嘗試將具有相依性的所有成品一起保留在相同的應用程式中。 但是，這個作法不一定總是可行。 中所述[成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)，大多數的成品類型必須是唯一的 BizTalk 群組中。 您不能在相同群組的兩個不同應用程式中有相同的成品，即使當這兩個應用程式包含的成品相依於相同的成品時，也是如此。  
  
 當發生這種情況時，您可以將所需的成品加入到一個應用程式中，然後加入該應用程式的參考 (從包含相依於它之成品的任何其他應用程式參考該應用程式)。 當您加入應用程式的參考時，該應用程式中的成品可以使用它所參考之應用程式中的任何成品。 如需新增參考的指示，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
 下列圖表說明兩個 BizTalk 應用程式，這兩個應用程式各自都相依於第三個應用程式中的成品。 「訂單處理」應用程式會使用「結構描述」應用程式中所包含的 Schema1，好讓「訂單處理」應用程式包含此「結構描述」應用程式的參考。 「抵押貸款」應用程式會使用同樣包含在「結構描述」應用程式中的 Schema2，同樣地，前者的應用程式也會包含後者的參考。  
  
 ![兩個應用程式參考第三個應用程式](../core/media/applicationdependencies.gif "ApplicationDependencies")  
  
 加入從某個應用程式到另一個應用程式的參考，會在這兩個應用程式之間建立相依性，此相依性會影響您部署和管理這兩個應用程式的方式。 本主題稍後所述的應用程式相依性的各種作用，因為我們建議您遵循新增成品至應用程式的最佳作法中所述[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
 下列圖表將說明當有相依性連鎖時，與更新組件有關的步驟，而且相依於所更新之組件的所有組件都會存在於相同的應用程式中。  
  
 ![更新具有相依性的組件](../core/media/simpleadminredeploy.gif "SimpleAdminRedeploy")  
  
 下列圖表將說明當所更新之組件有相依性連鎖時，與更新組件有關的步驟，而且其中一個相依組件存在於不同的應用程式中。  
  
 ![更新具有外部相依性的組件](../core/media/complexadminredeploy.gif "ComplexAdminRedeploy")  
  
> [!NOTE]
>  在更新組件之前執行完全停止的理由，是因為這樣做會自動取消登錄此協調流程，並停止和終止所有訊息。 如果您需要繼續處理訊息，您可以部署相同組件的另一個版本，這樣就不需要停止和終止訊息。 如需詳細資訊，請參閱[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。  
  
 應用程式之間的相依性可能會產生以下的作用：  
  
-   **停止成品。** 如果您停止一個應用程式中另一個應用程式所相依的成品 (這可能是停止整個應用程式所產生的結果)，則相依的應用程式將無法正確運作。 如需停止應用程式的詳細資訊，請參閱[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  
  
-   **移除或變更成品的狀態。** 當您加入從某個應用程式到另一個應用程式的參考，並針對另一個應用程式所相依之成品的狀態進行任何變更或移除該成品時，具有相依性的應用程式將無法正確運作。 如需有關如何變更成品狀態的詳細資訊，請參閱中適當的成品[管理成品](../core/managing-artifacts.md)。  
  
-   **匯入具有相依性的應用程式。** 如果您想要將應用程式匯入到不同的 BizTalk 群組，並於該群組中執行它，您也必須匯入此應用程式所相依的任何成品。 若要這樣做，您可以先匯入另一個應用程式，或是將所需的成品加入到需要它的應用程式中。 如需有關匯入應用程式的詳細資訊，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
    > [!NOTE]
    >  BizTalk Server 會比對來源和目的地 BizTalk 群組中的應用程式名稱，以驗證應用程式的識別。 但是，它不會驗證您的應用程式相依的成品是否包含在其中。 當您匯入具有相依性的應用程式和應用程式所參考時，我們建議您確認參考的應用程式包含成品的必要的成品。  
  
-   **匯入具有其參照的應用程式。** 如果要匯入的應用程式與另一個應用程式中的成品相依，則必須加入此應用程式的參考。 匯入精靈有提供這個選項。 如果您使用 BTSTask 的 ImportApp 命令，不過，您必須加入參考匯入之後，應用程式中所述[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。 雖然 BizTalk Server 會驗證參考的應用程式是否存在，但我們還是建議您採取另一個步驟，也就是驗證所參考的應用程式是否包含必要的成品。  
  
-   **安裝具有相依性的應用程式。** 當您安裝應用程式時，也必須安裝它所相依的任何應用程式。 當您安裝與某個成品有相依性的應用程式 (例如包含在另一個應用程式中的 BizTalk 組件) 時，您必須先安裝包含該成品的應用程式。 例如，如果您想要安裝應用程式 A，而它相依於應用程式 B 中的組件，則您必須先安裝應用程式 B。 然後您就可以安裝應用程式 a。如需有關如何安裝應用程式的詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
-   **移動成品。** 當您將成品移到新的應用程式時，除非新的應用程式有參考移動之成品所相依之成品的所在應用程式，否則也會移動該成品所相依的其他任何成品。 此外，相依於移動之成品的任何成品也會移動，除非包含這些成品的應用程式有參考新的應用程式。 當您移動成品時，系統會為您顯示也將一併移動之其他成品的清單。 如需移動成品的指示，請參閱[如何將成品移至不同的應用程式](../core/how-to-move-an-artifact-to-a-different-application.md)。  
  
-   **另一個應用程式中的成品相依於它時，請更新成品。** 當您更新應用程式中的某個成品，而此成品相依於相同應用程式中的另一個成品時，BizTalk Server 會自動處理此相依成品的解除部署和重新部署工作。 但是，如果您想要更新某個應用程式中的某個成品，而另一個應用程式中的成品與它相依時，您就必須手動解除部署和重新部署此相依成品，如下所示：  
  
    1.  停止、取消登錄和解除繫結此相依成品。  
  
    2.  更新它所相依的成品。  
  
    3.  繫結、登錄和啟動此相依成品。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)