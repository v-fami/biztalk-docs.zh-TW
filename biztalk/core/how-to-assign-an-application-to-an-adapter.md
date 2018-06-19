---
title: 如何指派給配接器應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f1ea2773-c53c-40a0-a312-015191746451
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5052d06576988ed71da8458a9d55115fb0b1c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246670"
---
# <a name="how-to-assign-an-application-to-an-adapter"></a>如何指派給配接器應用程式
為了在本機應用程式和遠端伺服器之間處理資訊，必須將一個或更多的應用程式指派給配接器。  
  
### <a name="to-assign-an-application-to-an-adapter"></a>指派應用程式給配接器  
  
1.  使用  `ISSOPSAdmin.AssignApplicationToAdapter` 將應用程式加入至配接器。  
  
2.  您可以使用 `ISSOAdmin.GetApplicationsForAdapter` 來擷取目前指派給配接器的應用程式清單。  
  
3.  完成之後，您就可以使用 `ISSOPSAdmin.RemoveApplicationFromAdapter` 從配接器移除應用程式。