---
title: 如何匯出至.msi 檔案的應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7179e86-aa55-426b-a0db-19229ca5625a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600118718585401d9ba6c3158b6510af55c53e74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297766"
---
# <a name="how-to-export-an-application-to-an-msi-file"></a>如何匯出至.msi 檔案的應用程式
您可以使用匯出 MSI 檔案精靈或 BTSTask，應用程式成品匯出至.msi 檔案將應用程式匯入新的 BizTalk 群組。 此程序也會將執行它的電腦上安裝應用程式。  
  
## <a name="exporting-application-bindings-in-an-msi-file"></a>匯出應用程式.msi 檔案中的繫結  
 當您匯出至.msi 檔案的應用程式時，您可以選取要匯出哪些資源。 這些資源可以包含的全部或子集已部署的組件或匯出繫結可供使用。  
  
 若要讓您更輕鬆地匯入您的開發環境的應用程式在稍後變更或新增項目，您可能想要匯出繫結每個應用程式，然後將其加入回應用程式。 當您設定與資源類型"BiztalkBinding 」 時，您可以加入額外的繫結檔案至.msi 檔案。 您將加入每個繫結檔案，您必須指定應該套用這些繫結至環境名稱 （文字欄位）。 然後在匯入時，您會詢問以選取目前匯環境名稱。 如果這些相符，則會套用至目標群組繫結檔案。 您也可以指定任何環境加入繫結檔案名稱，這會導致無條件地套用到所有環境的繫結的集合。  
  
 使用.msi 檔案會自動化功能可以否則有很多設定的手動工作。 在實際執行環境中，您可以輕鬆部署到多個 BizTalk 群組組件所傳輸的繫結，以及組件的組件。 如果您的應用程式包含大量的成品，您可以將匯出之成品的一些單一的 Windows Installer 套件，以及一些成一或多個其他 Windows Installer 封裝。  
  
 同時匯出應用程式，您應該考慮一些重點。 例如，您可以匯出所有應用程式中的成品或您想要加入或更新的成品。 如果您匯出檔案成品，請確定它是您想要在應用程式中使用的版本。 更多這類點以及匯出至.msi 檔案的 BizTalk 應用程式的詳細資訊，請參閱[如何匯出 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154848)(http://go.microsoft.com/fwlink/?LinkID=154848)。