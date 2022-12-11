# file-download

```
from django.http import FileResponse


class FileDownloadView(generics.RetrieveAPIView):
    queryset = models.File.objects.all()
    serializer_class = None

    def retrieve(self, request, *args, **kwargs):
        instance = self.get_object()
        file_path = instance.file.path
        file_name = instance.file.name
        response = FileResponse(open(file_path, 'rb'))
        response['Content-Disposition'] = 'attachment; filename=%s' % file_name
        return response
```
