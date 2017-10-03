---
title: "文件結構強化，一般檔案組合器管線元件中的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component], document structure
ms.assetid: 3ac75706-1d4d-443a-a4bf-af8f79a6a092
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb35c7b31eda69d03d532d13d975d618d4f36f76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="document-structure-enforcement-in-the-flat-file-assembler-pipeline-component"></a>一般檔案組合器管線元件中的文件結構強化
若在一般檔案組合器中明確參考的文件或信封結構描述，則一般檔案組合器可保證只會處理具有對應到參考的結構描述的訊息類型之文件。 即使所有其他文件可能具有已部署的結構描述，還是不會處理這些文件。  
  
> [!NOTE]
>  信封結構描述僅取自第一則訊息。 信封的屬性固定取自第一則訊息。