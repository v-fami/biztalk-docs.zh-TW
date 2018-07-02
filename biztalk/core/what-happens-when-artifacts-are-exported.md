---
title: 匯出成品時，會發生什麼事 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exporting, artifacts
- artifacts, exporting
ms.assetid: accc9a81-01fb-4da7-a5a5-167835d393a2
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4a4b83608c09ff08fd8536bcdac806e3299775b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977319"
---
# <a name="what-happens-when-artifacts-are-exported"></a>匯出成品時所產生的狀況
本主題描述匯出成品時所產生的狀況。 匯出成品的方法有三種，本主題將涵蓋這三種方法：  
  
-   將 BizTalk 應用程式及其成品匯出到 BizTalk .msi (Windows Installer) 檔案  
  
-   將原則匯出到 .xml 檔案  
  
-   將繫結匯出到 .xml 檔案  
  
## <a name="exporting-a-biztalk-application"></a>匯出 BizTalk 應用程式  
 當您匯出 BizTalk 應用程式以及其所包含的成品時，應用程式組態資訊和成品資料會匯出到 BizTalk .msi 檔案。 大部分的成品資料都是從 BizTalk 管理資料庫匯出，但是有下列幾個例外：  
  
- 原則資料會從該群組的規則引擎資料庫匯出。  
  
- 虛擬目錄資料如果未存在於管理資料庫中，則會從 Internet Information Services (IIS) Metabase 匯出。 當虛擬目錄尚未明確加入至應用程式就會發生的情況 (如中所述[如何將虛擬目錄新增至應用程式](../core/how-to-add-a-virtual-directory-to-an-application.md)) 或是有不到此群組，從.msi 檔案匯入應用程式從另一個 BizTalk 群組匯出。  
  
- 憑證資料如果未存在於管理資料庫中，則會從本機電腦上的「其他人」憑證存放區匯出。 當憑證尚未明確加入至應用程式就會發生的情況 (如中所述[如何將憑證新增至應用程式](../core/how-to-add-a-certificate-to-an-application.md)) 或是有不到這個群組的.msi 檔案匯入應用程式從另一個 BizTalk 群組匯出。 當您使用具有相關憑證的接收埠匯出應用程式時，將會匯出憑證。 匯出時將會從憑證中移除私密金鑰。  
  
  您可以使用這個 .msi 檔案，將應用程式的成品 (包括其所有資料) 匯入到另一個 BizTalk 群組的應用程式。 您也可以使用此 .msi 檔案，在電腦上安裝此應用程式。  
  
## <a name="exporting-a-policy"></a>匯出原則  
 當您使用管理主控台匯出 BizTalk 群組或應用程式的原則時，它會產生包含原則資訊的 .xml 原則檔案。 您可以將此原則檔案匯入另一個 BizTalk 群組，以便在該處建立此原則，好讓該群組中的應用程式可以使用它。 您也可以使用 BTSTask 匯出應用程式的原則資訊， 但是，BTSTask 並沒有可匯出原則 .xml 檔案的命令。 您可改為匯出只包含此原則的應用程式 .msi 檔案， 然後您可以將此 .msi 檔案匯入到另一個群組的應用程式中。  
  
## <a name="exporting-bindings"></a>匯出繫結  
 您可以使用管理主控台或 BTSTask 匯出 BizTalk 群組、應用程式或組件的繫結。 當您這樣做時，BizTalk Server 會產生一個 .xml 檔案，其中包含此群組、應用程式或組件的繫結資訊。 當您匯出繫結時，也可以一併匯出此群組的全域合作對象資訊。 之後您可以將此繫結檔案加入到應用程式，或是將它匯入到 BizTalk 群組或應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [會發生什麼事成品至應用程式部署期間](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [匯出 BizTalk 應用程式、 繫結和原則](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md)