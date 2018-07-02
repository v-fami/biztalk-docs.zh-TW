---
title: 建立應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b6e325c-a86f-419d-9a27-864f4f035507
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 772ba15d357715d5ceeca3c229167a96f7ef6c60
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987543"
---
# <a name="creating-an-application"></a>建立應用程式
有三種方式可建立 BizTalk 應用程式。 另外還有幾個選項命名、 參考及部署應用程式的成品。  
  
## <a name="creating-a-biztalk-application"></a>建立 BizTalk 應用程式  
 三種方式如下所示：  
  
1. 使用 BizTalk Server 管理主控台的 [新增應用程式] 命令或 BTSTask 命令列工具的 AddApp 命令，建立 BizTalk 應用程式。 如需使用這些命令的詳細資訊，請參閱 <<c0> [ 如何建立應用程式](http://go.microsoft.com/fwlink/?LinkId=155007)(http://go.microsoft.com/fwlink/?LinkId=155007)。  
  
2. 匯入已經從另一個應用程式匯出的 .msi 檔案。 如果目前 BizTalk 群組中沒有此應用程式，則會在目前 BizTalk 群組中自動建立此應用程式以及它的成品。 如需有關如何匯入應用程式的詳細資訊，請參閱 <<c0> [ 如何匯入 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154827)(http://go.microsoft.com/fwlink/?LinkID=154827)。  
  
3. 從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式。 如果在 Visual Studio 中專案的部署屬性中指定的應用程式不存在於目前的 BizTalk 群組中，將會自動予以建立。 如需部署組件從 Visual Studio 的詳細資訊，請參閱[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。  
  
   若要部署應用程式使用.msi 檔，目的地應用程式不需要存在，但將會自動建立。 不過，將繫結匯入到另一個應用程式，接收端應用程式必須存在。 如果沒有，您需要建立藉由執行其中一個上面所列的程序。  
  
   如需有關建立應用程式所需的特定步驟的詳細資訊，請參閱 <<c0> [ 如何建立應用程式](http://go.microsoft.com/fwlink/?LinkId=155007)(http://go.microsoft.com/fwlink/?LinkId=155007)。  
  
## <a name="application-options"></a>應用程式選項  
 然後再建立新的應用程式，您應該執行下列作業：  
  
-   判斷應用程式的 BizTalk 群組內是唯一的名稱。  
  
-   將參考加入新的應用程式，以包含您想要在新的應用程式中重複使用的成品的任何應用程式。 如需應用程式之間的相依性的詳細資訊，請參閱[相依性和應用程式部署](http://go.microsoft.com/fwlink/?LinkId=155008)(http://go.microsoft.com/fwlink/?LinkId=155008)。  
  
-   決定是否要將一些成品部署到個別的應用程式，例如，共用的成品應部署到他們自己個別的應用程式。